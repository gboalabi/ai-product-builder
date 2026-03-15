# Repository Structure

## Top-Level Layout
- `components/` — React UI modules (dashboards, cards, modal, navigation, charts)
- `core/` — backend-adjacent core modules (DB client/repos, providers, scoring, types)
- `server/` — Express API server and Gemini workflow integration
- `scripts/` — ingestion, scoring, validation, and DB utility scripts
- `diagnostics/` — diagnostics tooling for runtime/trend behavior checks
- `docs/` — governance, roadmap, architecture targets, and process documentation
- `data/` — local data artifacts (e.g., CSV inputs for import scripts)

## Major Directory Purposes

### `components/`
Contains product UI surfaces:
- discover view cards/charts,
- strategy modal,
- planner dashboard,
- agency dashboard.

### `core/db/`
Database implementation foundation:
- `client.ts` for pooled DB access/transactions,
- `migrations/` for additive schema changes,
- `repositories/` for batch insert/upsert/query helpers.

### `core/providers/`
Provider abstraction and adapters:
- interface contracts,
- TikTok provider scaffolding,
- TikTok Creative Center ingestion adapter.

### `core/scoring/`
Trend score computation logic and stage transformations (weighted/velocity/acceleration flows).

### `server/`
Runtime API surface:
- health,
- trend retrieval,
- watchlist,
- alerts,
- planner CRUD,
- AI trend/strategy integration.

### `scripts/`
Operational pipeline entry points:
- ingest TikTok Creative Center signals,
- import Google Trends CSV,
- compute multiple scoring stages,
- validate and seed data,
- apply/reset/check DB migrations.

## Module Organization Pattern
- UI concerns are separated in `components` and typed through shared `types.ts`.
- API consumption logic is centralized in `geminiService.ts`.
- Persistent data concerns are segmented into migration + repository modules.
- Pipeline tasks are intentionally separated into CLI scripts rather than embedded server jobs.
