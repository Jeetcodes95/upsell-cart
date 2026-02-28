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
