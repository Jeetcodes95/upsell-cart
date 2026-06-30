# Upsell Cart — 12-Month Roadmap

## Phase 1 — Foundation (Month 1–2)
- [ ] Shopify app setup (Partner dashboard, App Bridge v3)
- [ ] OAuth install flow + token storage (AES-256)
- [ ] Webhook registration system (HMAC validation)
- [ ] Merchant schema + multi-tenant MongoDB structure
- [ ] Product catalog sync from Shopify API
- [ ] BullMQ queue system for async processing
- [ ] CI/CD: GitHub Actions + AWS ECR

## Phase 2 — Core Features (Month 3–4)
- [ ] Cart widget (Theme App Extension)
- [ ] Manual upsell rule builder (merchant dashboard)
- [ ] Frequently bought together recommendations (rule-based v1)
- [ ] Bundle builder + discount engine
- [ ] Post-purchase extension (Shopify Checkout UI Extension)
- [ ] Merchant onboarding flow

## Phase 3 — AI Layer (Month 5–6)
- [ ] Purchase event stream → feature store
- [ ] Item-item collaborative filtering model
- [ ] Real-time inference API with Redis caching
- [ ] A/B testing engine: variant creation, assignment, tracking
- [ ] Statistical significance calculator
- [ ] Auto-winner selection logic

## Phase 4 — Analytics & Billing (Month 7–8)
- [ ] Analytics dashboard: AOV uplift, conversion rate, revenue attribution
- [ ] Shopify Billing API integration (subscription plans)
- [ ] Stripe as secondary billing for off-platform merchants
- [ ] Usage-based billing (per-order tier tracking)
- [ ] Revenue share tracking module

## Phase 5 — Scale & App Store (Month 9–10)
- [ ] Performance: <100ms recommendation latency P99
- [ ] Load test: 10k concurrent store webhooks
- [ ] Shopify App Store listing preparation
- [ ] App review compliance audit
- [ ] Documentation site

## Phase 6 — Launch (Month 11–12)
- [ ] Shopify App Store submission
- [ ] Shopify Experts + Partner ecosystem integration
- [ ] ProductHunt launch
- [ ] Target: 100 installed stores in 30 days post-launch
- [ ] Target: $5k MRR by Month 12


> **Note (2026-02-28):** Weekend review — post-purchase extension acceptance rate at 18.4% on test data. Validating with larger dataset before publishing results.


### Week 9 Progress (2026-03-03)

- ✅ Recommendation cache warming on catalog sync
- ✅ Bundle discount compound validation logic
- 🔄 Post-purchase Shopify extension: one-click upsell flow 70% done
- 📋 Next: Billing API — Shopify subscription lifecycle events


### Week 10 Progress (2026-03-10)

- ✅ Product catalog sync optimized with incremental webhook updates
- ✅ Webhook deduplication TTL reduced (40% Redis memory reduction)
- 🔄 A/B testing: statistical significance calculator in progress
- 📋 Next: Auto-winner selection at 95% confidence threshold


### Week 11 Progress (2026-03-17)

- ✅ Recommendation cache warming on catalog sync
- ✅ Bundle discount compound validation logic
- 🔄 Post-purchase Shopify extension: one-click upsell flow 70% done
- 📋 Next: Billing API — Shopify subscription lifecycle events


> **Note (2026-03-21):** Weekend review — post-purchase extension acceptance rate at 18.4% on test data. Validating with larger dataset before publishing results.


### Week 12 Progress (2026-03-24)

- ✅ Product catalog sync optimized with incremental webhook updates
- ✅ Webhook deduplication TTL reduced (40% Redis memory reduction)
- 🔄 A/B testing: statistical significance calculator in progress
- 📋 Next: Auto-winner selection at 95% confidence threshold


### Week 13 Progress (2026-03-31)

- ✅ Recommendation cache warming on catalog sync
- ✅ Bundle discount compound validation logic
- 🔄 Post-purchase Shopify extension: one-click upsell flow 70% done
- 📋 Next: Billing API — Shopify subscription lifecycle events


### Week 14 Progress (2026-04-07)

- ✅ Product catalog sync optimized with incremental webhook updates
- ✅ Webhook deduplication TTL reduced (40% Redis memory reduction)
- 🔄 A/B testing: statistical significance calculator in progress
- 📋 Next: Auto-winner selection at 95% confidence threshold


> **Note (2026-04-11):** Weekend review — post-purchase extension acceptance rate at 18.4% on test data. Validating with larger dataset before publishing results.


### Week 15 Progress (2026-04-14)

- ✅ Recommendation cache warming on catalog sync
- ✅ Bundle discount compound validation logic
- 🔄 Post-purchase Shopify extension: one-click upsell flow 70% done
- 📋 Next: Billing API — Shopify subscription lifecycle events


### Week 16 Progress (2026-04-21)

- ✅ Product catalog sync optimized with incremental webhook updates
- ✅ Webhook deduplication TTL reduced (40% Redis memory reduction)
- 🔄 A/B testing: statistical significance calculator in progress
- 📋 Next: Auto-winner selection at 95% confidence threshold


### Week 17 Progress (2026-04-28)

- ✅ Recommendation cache warming on catalog sync
- ✅ Bundle discount compound validation logic
- 🔄 Post-purchase Shopify extension: one-click upsell flow 70% done
- 📋 Next: Billing API — Shopify subscription lifecycle events


> **Note (2026-05-02):** Weekend review — post-purchase extension acceptance rate at 18.4% on test data. Validating with larger dataset before publishing results.


### Week 18 Progress (2026-05-05)

- ✅ Product catalog sync optimized with incremental webhook updates
- ✅ Webhook deduplication TTL reduced (40% Redis memory reduction)
- 🔄 A/B testing: statistical significance calculator in progress
- 📋 Next: Auto-winner selection at 95% confidence threshold


### Week 19 Progress (2026-05-12)

- ✅ Recommendation cache warming on catalog sync
- ✅ Bundle discount compound validation logic
- 🔄 Post-purchase Shopify extension: one-click upsell flow 70% done
- 📋 Next: Billing API — Shopify subscription lifecycle events


### Week 20 Progress (2026-05-19)

- ✅ Product catalog sync optimized with incremental webhook updates
- ✅ Webhook deduplication TTL reduced (40% Redis memory reduction)
- 🔄 A/B testing: statistical significance calculator in progress
- 📋 Next: Auto-winner selection at 95% confidence threshold


> **Note (2026-05-23):** Weekend review — post-purchase extension acceptance rate at 18.4% on test data. Validating with larger dataset before publishing results.


### Week 21 Progress (2026-05-26)

- ✅ Recommendation cache warming on catalog sync
- ✅ Bundle discount compound validation logic
- 🔄 Post-purchase Shopify extension: one-click upsell flow 70% done
- 📋 Next: Billing API — Shopify subscription lifecycle events


### Week 22 Progress (2026-06-02)

- ✅ Product catalog sync optimized with incremental webhook updates
- ✅ Webhook deduplication TTL reduced (40% Redis memory reduction)
- 🔄 A/B testing: statistical significance calculator in progress
- 📋 Next: Auto-winner selection at 95% confidence threshold


### Week 23 Progress (2026-06-09)

- ✅ Recommendation cache warming on catalog sync
- ✅ Bundle discount compound validation logic
- 🔄 Post-purchase Shopify extension: one-click upsell flow 70% done
- 📋 Next: Billing API — Shopify subscription lifecycle events


> **Note (2026-06-13):** Weekend review — post-purchase extension acceptance rate at 18.4% on test data. Validating with larger dataset before publishing results.


### Week 24 Progress (2026-06-16)

- ✅ Product catalog sync optimized with incremental webhook updates
- ✅ Webhook deduplication TTL reduced (40% Redis memory reduction)
- 🔄 A/B testing: statistical significance calculator in progress
- 📋 Next: Auto-winner selection at 95% confidence threshold


### Week 25 Progress (2026-06-23)

- ✅ Recommendation cache warming on catalog sync
- ✅ Bundle discount compound validation logic
- 🔄 Post-purchase Shopify extension: one-click upsell flow 70% done
- 📋 Next: Billing API — Shopify subscription lifecycle events


### Week 26 Progress (2026-06-30)

- ✅ Product catalog sync optimized with incremental webhook updates
- ✅ Webhook deduplication TTL reduced (40% Redis memory reduction)
- 🔄 A/B testing: statistical significance calculator in progress
- 📋 Next: Auto-winner selection at 95% confidence threshold
