
## [Unreleased] — 2026-02-25

### Performance
- Webhook dedup TTL: 24h → 6h (Redis memory −40%)
- Recommendations: cache warming on catalog sync (70% warm-cache hit rate)

### Fixed
- Bundle discount: prevent compound overlap with Shopify automatic discounts


## [Unreleased] — 2026-03-04

### Added
- Post-purchase extension: one-click upsell within Shopify checkout flow
- Shopify Billing API: subscription lifecycle webhook handlers
- Revenue attribution: upsell_source tagging on attributed order lines

### Changed
- A/B variant assignment: murmur hash → FNV-1a (uniform distribution)
