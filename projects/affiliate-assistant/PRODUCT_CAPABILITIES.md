# Product Capabilities Audit — IKIRA Affiliate Assistant

## Core Platform Capabilities (Current Implementation)

1. **Guided product discovery**
   - Home page merchandising sections and product grids.
   - Basic client-side filtering by budget and rating.

2. **Decision-support workflow**
   - Multi-step quiz UI that collects user intent signals.
   - Recommendation-style results page generated from local mock logic.

3. **Bundle composition workflow**
   - Budget-driven bundle construction logic in the frontend.
   - Kit total visualization and checkout/save actions (simulated).

4. **Comparative shopping workflow**
   - Add/remove products to compare (up to 4 items).
   - Side-by-side spec table with difference highlighting.

5. **Story and creator storefront discovery**
   - Story modal flow linking to product detail pages.
   - Storefront list/detail pages with curated products.

6. **Admin operations prototype**
   - Dashboard tabs for affiliate programs, feed uploads, shortlinks, payouts, and branding.
   - These modules currently operate as front-end simulations.

---

## Key Workflows

### Consumer Workflows
- Browse products → open product detail → click merchant CTA.
- Take quiz → view suggested picks → move to bundles.
- Build bundle under budget → simulate checkout/save flow.
- Compare multiple products → evaluate specs → click buy link.
- Explore stories/storefronts → navigate to products.

### Admin Workflows (Prototype)
- View and add affiliate programs in UI state.
- Simulate feed upload and monitor static status list.
- Create shortlinks in local state.
- View payout summary cards and export toast action.
- Adjust theme settings and preview appearance changes.

---

## Generation Process (What Is Actually Implemented)

### Recommendation/Selection Generation
- **Quiz results:** deterministic local rendering using mock products.
- **Bundles:** client-side rules using product categories and budget thresholds.
- **Compare view:** generated from selected products in context state.

### Not Implemented (Generation Backends)
- No ML or AI recommendation service.
- No scoring engine service.
- No backend personalization pipeline.

---

## Governance Features

### Implemented
- Global FTC disclosure component rendered in the layout.
- Basic role-themed admin interface (UI only).

### Partially Represented / Not Implemented
- No role-based authorization enforcement.
- No audit trail for admin actions.
- No policy engine or moderation workflows.

---

## Analytics Features

### Implemented
- Minimal user feedback via toasts for key interactions.

### Not Implemented
- No event ingestion/analytics backend.
- No metrics dashboard backed by tracked events.
- No funnel/conversion attribution data processing.

---

## Major Product Modules

- **Discovery Module:** home merchandising + filters.
- **Quiz Module:** guided preference capture + recommendation display.
- **Bundles Module:** budget-based kit assembly.
- **Compare Module:** product comparison matrix.
- **Product Detail Module:** product info, price history sparkline, actions.
- **Stories Module:** story-first product exploration.
- **Storefront Module:** creator-centric shopping pages.
- **Admin Module:** operational surface for affiliate/feed/shortlink/payout/theme controls.
