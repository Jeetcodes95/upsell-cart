# Dev Log — Week 11

**Product**: Upsell Cart  
**Date**: 2026-03-06  
**Author**: JeetCodes95  

---

## This Week

### Completed
- Webhook deduplication TTL reduced: 24h → 6h (Redis memory −40%)
- Recommendation cache warming on product catalog sync events
- A/B testing: FNV-1a hash for uniform variant assignment (<0.5% distribution bias)

### In Progress
- Post-purchase Shopify extension (one-click upsell without payment re-entry)
- Statistical significance engine (Chi-squared test implementation)

### Architecture Note

Moved recommendation model inference out of the request path entirely. Flow:
1. Cart page loads → sends cart hash to `/recommend` API
2. API returns cached result immediately (if warm) or queues computation
3. Widget polls `/recommend/status/:hash` until result ready
4. Result cached for 15 minutes per cart composition

Result: P99 cart page impact dropped from 320ms to 42ms.

---

## Metrics

| Commits | Test Coverage | P99 Rec. Latency | Webhook Queue Depth |
|---|---|---|---|
| 16 | 62% | 42ms | <20 |
