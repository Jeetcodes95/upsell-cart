# Upsell Cart — AI-Powered Shopify AOV Optimization Engine

> **Intelligent upsells, cross-sells, and checkout optimization — built for Shopify merchants who take revenue seriously.**

[![Shopify Partners](https://img.shields.io/badge/Shopify-Partner-96BF48?logo=shopify&logoColor=white)](https://partners.shopify.com)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-0.1.0--alpha-orange)](CHANGELOG.md)

---

## The Problem

Shopify merchants lose 60–80% of potential revenue on every transaction. Customers who **would** buy more, don't — because they're never shown the right product at the right moment.

Existing upsell apps are static rule engines. They fire when a product is added, regardless of context, cart composition, or customer history.

**Upsell Cart is different.**

---

## What We Built

An AI-driven upsell and checkout optimization engine that:

- Analyzes cart composition, purchase history, and behavioral signals in real time
- Generates dynamic product recommendations per customer segment
- Runs A/B tests on upsell placements to eliminate guesswork
- Handles post-purchase offers within Shopify's checkout extension framework
- Provides a merchant analytics dashboard with AOV uplift attribution

---

## Core Features

### 🤖 AI Recommendation Engine
- Cart-aware product recommendations using collaborative filtering
- Real-time inference via lightweight model served from Node.js
- Cold-start fallback: top-sellers by category + manual merchant rules
- Segment-based personalization (new vs returning vs high-LTV)

### 🛒 Cart Page Optimization
- Sticky upsell widgets: "Frequently bought together", "Complete the look"
- Dynamic bundle builder — merge products into discounted sets
- Cart abandonment detection → trigger exit-intent modal

### 📦 Smart Bundling
- Rule-based bundle creation (merchant-configured)
- AI-suggested bundles from purchase correlation
- Bundle discount engine (fixed, percentage, BOGO)

### 💳 Post-Purchase Upsell
- Native Shopify post-purchase extension
- One-click upsell — no re-entry of payment details
- Trigger within 60s of order confirmation

### 🧪 A/B Testing Engine
- Variant creation per placement (widget, modal, inline)
- Traffic split (50/50 or custom)
- Statistical significance tracking
- Auto-winner selection at 95% confidence

### 📊 Analytics Dashboard
- AOV before/after uplift per upsell campaign
- Conversion rate per placement
- Revenue attribution heatmap
- Store-level and campaign-level breakdowns

---

## Tech Stack

| Layer | Technology |
|---|---|
| App Framework | Next.js 14 (merchant dashboard) |
| App Backend | Node.js + Express + TypeScript |
| Shopify Integration | Shopify App Bridge, Polaris, Checkout UI Extensions |
| Database | MongoDB Atlas (multi-tenant) |
| Queue | BullMQ + Redis |
| AI/Recommendations | Node.js lightweight model + Python ML service |
| Billing | Stripe + Shopify Billing API |
| Infra | Docker, AWS ECS, Vercel (dashboard) |
| CI/CD | GitHub Actions |

---

## Repository Structure

```
upsell-cart/
├── backend/
│   ├── src/
│   │   ├── shopify/           # Webhook handlers, API client
│   │   ├── recommendations/   # AI engine + rules
│   │   ├── bundles/           # Bundle logic
│   │   ├── abtesting/         # Experiment engine
│   │   ├── billing/           # Stripe + Shopify billing
│   │   └── analytics/
│   └── Dockerfile
├── frontend/
│   ├── app/                   # Next.js merchant dashboard
│   │   ├── dashboard/
│   │   ├── campaigns/
│   │   ├── bundles/
│   │   ├── analytics/
│   │   └── settings/
│   └── extensions/
│       ├── cart-widget/       # Shopify Theme App Extension
│       └── post-purchase/     # Shopify Post-Purchase Extension
├── architecture/
├── docs/
├── logs/
├── docker-compose.yml
├── ROADMAP.md
└── README.md
```

---

## Shopify App Marketplace Positioning

- Category: Marketing → Upselling and Cross-Selling
- Target: Shopify Plus + Growth merchants (GMV $100k/year+)
- Pricing: Tiered SaaS (per-store subscription + revenue share option)

---

*Built by [JeetCodes95](https://github.com/JeetCodes95) | AI SaaS Architect for Commerce*
