# Project Overview — IKIRA Affiliate Assistant

## Project Name
**IKIRA Affiliate Assistant**

## Purpose
IKIRA Affiliate Assistant is a creator-commerce web application concept focused on helping users discover, evaluate, and purchase creator gear (audio/video equipment) while supporting affiliate attribution workflows.

## Problem It Solves
Shoppers and creators often face fragmented decision-making across reviews, marketplaces, and influencer recommendations. This system centralizes:
- guided product discovery,
- quick side-by-side comparison,
- creator-curated storefront browsing,
- and shortlink-based affiliate redirection.

## Target Users
- **Consumers / aspiring creators:** users selecting gear for podcasting, streaming, and content creation.
- **Creators:** users curating storefronts and potentially benefiting from rev-share.
- **Platform admins/operators:** users managing affiliate programs, feeds, shortlinks, payouts, and branding.

## Key Capabilities (Implemented in Current Repo)
- Multi-route React SPA (home, quiz, bundles, compare, stories, storefronts, admin, product detail, go redirect page).
- Product discovery UI with filters and merchandising sections.
- Quiz-driven recommendation experience (UI flow).
- Bundle builder with budget slider and mock bundle composition logic.
- Product comparison with up to 4 items via shared context state.
- Product details view with specs, pros/cons, pricing visualization, and CTA links.
- Creator storefront listing/detail views and story-style shopping UI.
- Admin dashboard tabs for affiliate hub, feeds, shortlinks, payouts, and theme controls (UI-level mock modules).

## Current Maturity Level
**Early-stage frontend prototype / clickable product simulation.**

The repository demonstrates a coherent product interface and user journey modeling, but core production platform layers are not implemented here (backend services, persistent data, auth, real provider integrations, jobs/workers, analytics pipeline, AI orchestration runtime).

## Summary of How the System Works
The app is built as a Vite + React + TypeScript single-page application using React Router and local component/context state. Most behavior is driven by static mock datasets (`data/mockData.ts`) and UI interactions (toasts, tabs, filters, slider state, modal state). Product purchase paths currently route to `/go/:slug` UI route, which simulates redirect behavior in-page rather than performing server-side resolution/attribution. Overall, the implemented system functions as a polished UX prototype aligned to a broader platform vision documented in `/docs`.
