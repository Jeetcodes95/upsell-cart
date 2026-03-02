# Architecture: Upsell Cart System Design

## Shopify Webhook System

```
Shopify Store
  │
  ├── PRODUCT_CREATED          → Sync product catalog
  ├── PRODUCT_UPDATED          → Update catalog + re-index
  ├── ORDERS_FULFILLED         → Purchase signal for ML training
  ├── ORDERS_PAID              → Trigger post-purchase flow
  ├── APP_SUBSCRIPTIONS_UPDATE → Billing state sync
  └── CARTS_UPDATE             → Real-time cart composition tracking
```

### Webhook Handler Architecture

```typescript
// Verify Shopify HMAC before processing
export const verifyShopifyWebhook = (req: Request): boolean => {
  const hmac = req.headers['x-shopify-hmac-sha256'];
  const body = req.rawBody;
  const computedHmac = createHmac('sha256', process.env.SHOPIFY_SECRET)
    .update(body)
    .digest('base64');
  return timingSafeEqual(Buffer.from(hmac), Buffer.from(computedHmac));
};

// Idempotent webhook processing via Redis deduplication
export const processWebhook = async (topic: string, shopDomain: string, payload: unknown) => {
  const eventId = `wh:${shopDomain}:${topic}:${hashPayload(payload)}`;
  const isDuplicate = await redis.set(eventId, '1', 'EX', 86400, 'NX');
  if (!isDuplicate) return;

  await webhookQueue.add(topic, { shopDomain, payload }, { jobId: eventId });
};
```

## Multi-Tenant Merchant Isolation

Each Shopify store (merchant) maps to a `merchantId`. All data collections are scoped by `merchantId`. OAuth tokens are encrypted at rest using AES-256.

```typescript
interface MerchantConfig {
  merchantId: string;
  shopDomain: string;
  accessToken: string;       // AES-256 encrypted
  scopes: string[];
  billingPlan: 'starter' | 'growth' | 'scale';
  isActive: boolean;
  installedAt: Date;
}
```

## AI Recommendation Engine

### Data Pipeline

```
Purchase Events → Feature Store (Redis) → Model Inference → Recommendations
     ↑                                          ↓
Shopify Orders API                    Cached per merchantId + cartHash (15 min TTL)
```

### Collaborative Filtering (v1 — Item-Item)

```python
# ai-service/recommendations/collaborative.py
import numpy as np
from scipy.sparse import csr_matrix
from sklearn.metrics.pairwise import cosine_similarity

class ItemItemRecommender:
    def __init__(self):
        self.similarity_matrix = None
        self.product_index = {}
    
    def fit(self, purchase_matrix: csr_matrix, products: list):
        self.similarity_matrix = cosine_similarity(purchase_matrix.T)
        self.product_index = {p['id']: i for i, p in enumerate(products)}
    
    def recommend(self, cart_product_ids: list, n: int = 5) -> list:
        scores = np.zeros(self.similarity_matrix.shape[0])
        for pid in cart_product_ids:
            if pid in self.product_index:
                idx = self.product_index[pid]
                scores += self.similarity_matrix[idx]
        # Exclude items already in cart
        for pid in cart_product_ids:
            if pid in self.product_index:
                scores[self.product_index[pid]] = -1
        top_indices = np.argsort(scores)[::-1][:n]
        return [products[i] for i in top_indices]
```

## A/B Testing Engine

```typescript
interface Experiment {
  id: string;
  merchantId: string;
  name: string;
  placement: 'cart_widget' | 'post_purchase' | 'exit_intent';
  variants: ExperimentVariant[];
  trafficSplit: number[];    // e.g., [50, 50]
  status: 'draft' | 'running' | 'completed';
  winnerVariantId?: string;
  startedAt?: Date;
  endedAt?: Date;
}

// Assign visitor to variant deterministically (by session hash)
export function assignVariant(sessionId: string, experiment: Experiment): string {
  const hash = murmurhash(sessionId + experiment.id) % 100;
  let cumulative = 0;
  for (let i = 0; i < experiment.variants.length; i++) {
    cumulative += experiment.trafficSplit[i];
    if (hash < cumulative) return experiment.variants[i].id;
  }
  return experiment.variants[0].id;
}
```

## Billing Integration

```
Shopify Billing API (App Subscriptions) + Stripe (for off-platform billing)

Plans:
  Starter  — $19/mo — Up to 500 orders/mo
  Growth   — $49/mo — Up to 5,000 orders/mo
  Scale    — $149/mo — Unlimited orders
  
Revenue Share Option (Growth+): 2% of attributed upsell revenue
```

## Scaling to 10k Stores

```
At 10k stores × avg 50 orders/day = 500k webhook events/day

Queue Architecture:
  webhook-ingestion:   20 concurrent workers, immediate
  recommendation:      10 concurrent workers, <100ms SLA
  analytics-ingestion: 5 concurrent workers, batch hourly
  billing-events:      2 concurrent workers, idempotent

MongoDB Indexes:
  db.recommendations.createIndex({ merchantId: 1, cartHash: 1 })
  db.orders.createIndex({ merchantId: 1, createdAt: -1 })
  db.experiments.createIndex({ merchantId: 1, status: 1 })

Redis Caching:
  - Recommendation results: 15-min TTL per cart composition
  - Merchant config: 60-min TTL (invalidated on plan change)
  - A/B variant assignments: session-scoped, 30-min TTL
```

## Security & Compliance

- HMAC webhook verification on every Shopify event
- OAuth tokens encrypted with AES-256-GCM (key in AWS KMS)
- Shopify App Review compliance: no data stored beyond required scope
- GDPR: Customer PII excluded from ML training data (only anonymized purchase patterns)
- Rate limiting: 40 req/s per store (Shopify API limit awareness)


## Updated: 2026-02-26

**A/B testing variant assignment:** Switched from murmur hash to FNV-1a for session-to-variant assignment. FNV-1a produces more uniform distribution on short session ID strings — reduces cluster bias in 50/50 splits from 3% to <0.5%.


## Updated: 2026-03-02

**Recommendation cache strategy:** Added cache warming on product catalog sync. When a merchant's catalog updates, the top-20 product recommendation sets are pre-computed and cached. Cold cart requests now hit warm cache 70% of the time.
