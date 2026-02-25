# Dev Log — Week 01

**Product**: Upsell Cart  
**Dates**: Feb 24 – Feb 28, 2026  
**Author**: JeetCodes95  

---

## Monday — Shopify App Bootstrap

- Shopify Partner account + app configured (app ID, client ID, secret)
- Shopify OAuth install flow implemented + tested on dev store
- Access token encrypted with AES-256-GCM, stored in MongoDB
- Webhook registration on install (orders/paid, products/update, carts/update, app/uninstalled)
- HMAC webhook verification middleware

**Commits:** 7

---

## Tuesday — Product Sync + Catalog

- Shopify REST API client (with retry + rate-limit awareness)
- Product catalog sync job (BullMQ): on install, syncs all products
- Product schema: title, variants, images, price, tags, vendor
- Webhook handler: products/updated → incremental catalog update
- Redis key: `catalog:{merchantId}` → 60-min TTL hot cache

**Commits:** 6

---

## Wednesday — Cart Widget Extension

- Shopify Theme App Extension scaffold
- Cart widget: vanilla JS + app proxy fetch for recommendations
- Manual rule engine v1: "if cart contains X, show Y" logic
- Merchant dashboard page: upsell rule builder CRUD
- Tested on Shopify dev store — widget rendering confirmed

**Commits:** 9

---

## Thursday — Recommendation Engine v1

- "Frequently bought together" calculation from order history
- Item-item co-occurrence matrix built from last 90 days of orders
- FastAPI recommendation endpoint: `POST /recommend` (cart → top 5 products)
- Redis cache: recommendations per `{merchantId}:{cartHash}` (15-min TTL)
- Cold-start fallback: return top-sellers by collection

**Commits:** 8

---

## Friday — Analytics Foundation

- Order event ingestion on `orders/paid` webhook
- AOV baseline calculation per merchant
- Upsell click tracking via pixel (analytics POST endpoint)
- Analytics dashboard: total revenue, avg AOV, upsell conversion rate (stub data)
- CI pipeline: lint + test all passing

**Commits:** 6

---

## Week 01 Summary

| Commits | 36 |
|---|---|
| Test coverage | 55% |
| Features shipped | OAuth, catalog sync, cart widget, rec engine v1, analytics ingestion |

**Next week:** Post-purchase extension, A/B testing foundation, Stripe billing integration
