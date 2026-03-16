# Architecture Overview (External-Friendly) — IKIRA Affiliate Assistant

## What this system is
IKIRA Affiliate Assistant is a web-based product discovery and affiliate-commerce experience for creator gear. It helps users find equipment, compare options, explore creator recommendations, and proceed to merchant purchase paths.

## Simple Architecture Explanation

### 1) Presentation Layer (implemented)
- A React single-page application powers all user experiences.
- Users can navigate between discovery, quiz, bundles, compare, stories, storefronts, product detail, and admin views.
- Shared UI components provide consistent design and interaction patterns.

### 2) Experience Logic Layer (implemented in frontend)
- Lightweight in-browser logic handles filtering, quiz steps, bundle generation rules, and comparison state.
- Mock datasets currently drive product/catalog/admin views.

### 3) Platform Services Layer (planned)
- The long-term platform design includes backend services for APIs, redirects, data ingestion, attribution, analytics, and payouts.
- In this repository, those service capabilities are represented as UI workflows and planning documentation, not production service code.

## How data currently flows
1. User interacts with the web interface.
2. Frontend state and mock datasets determine what appears on screen.
3. Purchase actions route to simulated affiliate redirect paths.

In short: current implementation demonstrates product behavior and UX patterns, while backend and data infrastructure are planned for subsequent phases.

## Why this architecture is useful for external audiences
- It shows strong product thinking and end-to-end user journey design.
- It separates immediate UX validation from later platform hardening.
- It provides a clear path from prototype to scalable production architecture.
