# Development Workflow Audit — IKIRA Affiliate Assistant

## Development Process (As Evidenced in Repo)

The current workflow appears to be **prototype-first UI development**:
- Build route-level screens and reusable components.
- Simulate end-to-end behaviors with mock data and local state.
- Validate user journeys visually in a frontend sandbox/dev server.
- Capture future production requirements in `/docs` for later backend implementation.

This creates a clear separation between:
1. what is currently interactive in the UI, and
2. what is planned for full platform implementation.

---

## Role of AI Tools

AI-related signals are currently **configuration-level** rather than runtime-level:
- Build config includes environment mapping for Gemini API variables.
- Repository README references AI Studio usage context.

However, no implemented AI module/service pipeline is present in source code. AI appears to be intended for later recommendation/explanation/routing features rather than active in current app behavior.

---

## Roadmap Structure

Based on code + docs alignment, the roadmap appears to follow:

1. **UX Prototype Phase (current):**
   - Rich frontend journeys across discovery, quiz, bundles, compare, stories, storefronts, and admin UI.

2. **MVP Platformization Phase (next):**
   - Add backend API, persistent data, auth/RBAC, redirect service, and basic ingestion.

3. **Scale & Intelligence Phase (later):**
   - Analytics pipeline, payout reconciliation, provider integrations, and AI orchestration enhancements.

---

## Documentation System

The repository shows a two-tier documentation model:

- **Implementation truth:** frontend codebase.
- **Strategic/target-state docs (`/docs`):** requirements, app flows, conceptual data model, and future architecture.

This is useful for planning, but requires explicit status labeling so readers can distinguish "implemented now" vs "planned design."

---

## Testing and Validation Approach

### Current Evidence
- No dedicated automated test suite is present in the repo structure.
- Validation appears to be manual UI/interaction verification during development.
- User feedback and interaction confirmations are surfaced via toasts and visual state changes.

### Recommended Next Workflow Upgrades
- Add unit tests for stateful logic (quiz, bundle composition, compare constraints).
- Add component/integration tests for key user flows.
- Add end-to-end tests for navigation and CTA paths.
- Introduce backend contract tests once API/services are implemented.
