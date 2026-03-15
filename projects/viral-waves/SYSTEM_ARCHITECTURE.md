# System Architecture

## Architecture Summary
Viral Waves is a full-stack application with:
- React frontend (single-page application)
- Node/Express API backend
- PostgreSQL persistence layer
- Script-driven ingestion/scoring pipeline
- LLM integration for strategy generation

The implementation currently runs as a web app + API service, with data pipeline jobs executed via CLI scripts (not always-on workers).

## Major System Components
- **Presentation Layer:** React dashboards for discovery, planner, and agency views
- **API Layer:** Express routes for trends, strategy generation, planner, watchlist, and alerts
- **Persistence Layer:** PostgreSQL with additive migration history
- **Data Pipeline Layer:** ingestion/import scripts + score computation scripts
- **AI Layer:** Gemini workflows for trend ideation and strategy generation

## Frontend Structure
- **App container:** coordinates view switching and data loading
- **Discover module:** renders ranked signal cards and watchlist actions
- **Planner module:** manages campaign drafts and alert configuration
- **Strategy modal:** requests AI strategy and can persist planner drafts
- **Agency module:** currently dashboard-style/stat display (limited live backend wiring)
- **Service client:** typed fetch wrapper with timeout/error handling for backend APIs

## Backend Structure
- **HTTP server:** Express app with JSON middleware and centralized error handling
- **Trend intelligence routes:**
  - DB-backed ranked signal retrieval
  - AI trend generation fallback/parallel path
- **Strategy route:** LLM-generated creative brief from selected trend context
- **Planner routes:** create/list/update/delete campaign drafts
- **Watchlist routes:** save/remove/list monitored entities
- **Alert routes:** create/update/list threshold rules and event evaluation

## Orchestration Layers
- **Request orchestration:** frontend calls API; backend composes DB + AI responses
- **Pipeline orchestration:** scripts run in sequence (ingest/import → weighted/velocity/acceleration scoring)
- **Alert orchestration:** evaluated on trend retrieval, with deduplicated daily alert event inserts

## AI Pipeline Components
- **Gemini client factory** with server-side API key loading
- **Prompt generation modules** for trend discovery and strategy generation
- **Response schema constraints** (JSON schema)
- **Timeout and retry wrapper** with retryable error classification
- **Structured parsing and validation** before returning API payloads

## Data Storage Approach
- **PostgreSQL relational model** with migrations for schema evolution
- Core tables include:
  - entity registry
  - daily metrics/features
  - daily rankings by stage
  - campaign drafts and signal snapshots
  - watchlist and alert rule/event records
- Repository modules provide batch upsert/insert patterns for ingestion performance.

## External Integrations
- **TikTok Creative Center (public trend pages):** script-driven signal ingestion
- **Google Trends CSV import:** manual/export-driven import path
- **Google Gemini API:** strategy generation and AI trend generation path

## Security / Exposure Notes
- LLM key usage is backend-side.
- Architecture includes local/dev-first database defaults and script tooling.
- This document intentionally omits secrets and internal/private endpoint specifics.
