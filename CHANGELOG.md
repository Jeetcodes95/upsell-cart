
## [Unreleased] — 2026-02-25

### Performance
- Webhook dedup TTL: 24h → 6h (Redis memory −40%)
- Recommendations: cache warming on catalog sync (70% warm-cache hit rate)

### Fixed
- Bundle discount: prevent compound overlap with Shopify automatic discounts
