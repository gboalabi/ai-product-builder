# Development Workflow

## Development Process
The repository uses an additive, milestone-oriented development style:
- frontend and backend evolve in parallel,
- schema changes are tracked through numbered migrations,
- pipeline behavior is exercised through explicit CLI scripts,
- roadmap/docs capture intended milestone state and scope boundaries.

Local development commonly runs:
- Vite frontend dev server
- Express API server
- PostgreSQL via Docker Compose

## Role of AI Tools
AI is used as an application capability, not only as a coding assistant:
- trend and strategy generation endpoints call Gemini workflows,
- JSON schema constraints and retry/timeout handling improve output reliability,
- AI output is integrated into planner workflows while persisted trend signals remain DB-backed.

## Roadmap Structure
The `/docs` roadmap and governance files define:
- milestone states,
- scope guards (what intentionally was not changed),
- verification expectations.

In practice, implementation is partially aligned with roadmap phases and has progressed into data-backed scoring and planner/alert features.

## Documentation System
- Root README provides setup and high-level architecture context.
- `/docs` provides governance, target architecture, data strategy, decision log, and verification templates.
- Documentation includes both target-state and historical planning context; implementation files remain the primary source of truth.

## Testing and Validation Approach
Validation in current implementation is script-driven and operationally oriented:
- diagnostics scripts for trend response behavior,
- smoke tests for Gemini integration,
- scoring validation scripts,
- DB status/reset/migration scripts.

The project has useful verification tooling but limited evidence of a comprehensive automated test suite (e.g., broad unit/integration CI coverage) in the current repository snapshot.
