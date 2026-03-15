# IKIRA AI Studio — Development Workflow

## Development Workflow
The project follows a phase-based, milestone-driven workflow. Features are scoped in roadmap phases, implemented iteratively, validated manually, and then refined through sub-phases that address stability, UX polish, and integration correctness.

Typical implementation pattern:
1. Define product intent and user flow in docs.
2. Build UI and service contracts behind stable interfaces.
3. Implement mock provider paths first to validate UX and state behavior.
4. Integrate real provider backends through adapter layers.
5. Add persistence/lifecycle features (library/projects/reuse).
6. Run regression checks and harden error handling.

## How AI Tools Are Used During Development
- AI-assisted coding is used within a documented phase structure rather than ad hoc edits.
- Documentation files act as guidance artifacts for implementation sequencing.
- AI support is used for rapid iteration, refactoring, and controlled integration tasks while preserving architecture boundaries.

## Project Roadmap Structure
- The roadmap is organized into sequential phases (foundation → generation pipelines → persistence → advanced workflows → future modules).
- Each phase includes:
  - Goal
  - Scope boundaries
  - Deliverables
  - Explicit “not in scope” constraints
  - Status tracking (completed / planned / blocked)

This structure supports predictable progress and makes the project portfolio-friendly.

## Documentation Approach
- Documentation is maintained as a first-class development artifact.
- Product requirements, app flow, backend architecture, and roadmap are used as source-of-truth references.
- Documents are written to be accessible to non-coders while still guiding technical implementation.

## Testing and Validation Approach
- Strong emphasis on end-to-end manual validation for feature correctness and UX continuity.
- Mock mode enables predictable local validation without external dependency failures.
- Integration phases include fail-loud behavior and explicit error-surface improvements.
- Ongoing roadmap indicates future expansion of formal hardening and broader automated validation.

## Deployment / Environment Strategy
- Local development runs web and backend concurrently.
- Environment variables are backend-scoped for sensitive provider configuration.
- Mock mode allows safe local development when provider credentials are unavailable.
- Provider integrations are abstracted behind backend services to support controlled rollout and future provider swaps.
