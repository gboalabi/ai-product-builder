# System Architecture Audit — IKIRA Affiliate Assistant

## Architecture Snapshot (As Implemented)
The current repository implements a **client-side web application prototype** built with Vite + React + TypeScript. It is structured as a single SPA with route-based pages and reusable UI modules, backed by static in-repo mock data.

There is no implemented server runtime in this repo for APIs, persistence, jobs, or AI orchestration.

---

## Major System Components

1. **Application Shell**
   - Global layout, navigation, theme toggle, and FTC disclosure.
2. **Feature Pages**
   - Home, Quiz, Bundles, Compare, Stories, Storefronts, Product, Admin, Go Redirect.
3. **Reusable UI Component Library**
   - Buttons, inputs, cards, tables, tabs, modals, badges, sliders, icons.
4. **State/Context Layer**
   - Theme context, compare context, toast context.
5. **Mock Data Layer**
   - Static product/storefront/story/admin records from `data/mockData.ts`.

---

## Frontend Structure

- **Entry/bootstrapping:** `index.tsx`, `App.tsx`
- **Routing:** React Router paths for primary flows (`/`, `/quiz`, `/bundles`, `/compare`, `/stories`, `/storefronts`, `/store/:id`, `/admin`, `/product/:id`, `/go/:slug`)
- **Pages:** route-level screens under `/pages`
- **Feature Components:** product cards, pricing sparkline, coupon/deal chips, admin modules
- **Layout:** global header + content container + compliance footer
- **Styling:** CSS + utility-style class usage

---

## Backend Structure

**Not implemented in this repository.**

No backend folders, API handlers, controllers, service-layer classes, or server entrypoints are present. The admin and redirect experiences are UI simulations.

---

## Orchestration Layers

### Implemented
- Client-side routing orchestration via React Router.
- UI state orchestration via React hooks and context providers.

### Not Implemented
- Workflow orchestration services.
- Queue/job orchestration.
- Domain service orchestration across backend components.

---

## AI Pipeline Components

### Observed in Code
- Build config maps a Gemini API key env variable into frontend build defines.

### Not Observed as Implemented
- No prompt pipelines.
- No model invocation modules.
- No AI service adapters.
- No inference, retrieval, ranking, or guardrail runtime logic.

Conclusion: AI pipeline is **not functionally implemented** in this codebase.

---

## Data Storage Approach

### Implemented
- In-memory client state (React state/contexts).
- Static mock data bundled with frontend.
- Limited browser localStorage usage (theme settings and brand/theme preview persistence).

### Not Implemented
- Database schema/migrations.
- Persistent domain storage for products, users, shortlinks, events, payouts, or quiz sessions.

---

## External Integrations

### Implemented (UI-level only)
- Placeholder affiliate redirect route (`/go/:slug`) and admin forms for program/shortlink/feed/payout functions.

### Not Implemented
- Real affiliate network adapters.
- Real feed ingestion sources.
- Analytics/event pipeline integrations.
- Auth providers.
- Payment/payout integrations.

---

## Target-State Context (From `/docs`, Not Current Implementation)
Supporting documents describe a future multi-service architecture (BFF/API gateway, redirect service, ingestion service, recommendation service, Postgres/Redis/object storage, eventing). These are strategic design targets and should be treated as planned architecture, not present architecture.
