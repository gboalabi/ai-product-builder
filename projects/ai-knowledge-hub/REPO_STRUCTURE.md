# AI Knowledge Hub — Repository Structure

## Overview
The repository is organized as a full-stack TypeScript project with a root frontend/admin app, a dedicated backend service, database migrations, runtime scripts, and connector assets.

## Major Directories

### `/backend/`
Primary backend service (Node.js + TypeScript + Express).

Key subdirectories:
- `/backend/src/api/` — public and admin API route handlers.
- `/backend/src/core/` — ingestion/retrieval/chunking/answer/embedding domain logic.
- `/backend/src/db/` — DB runtime bootstrap, repositories, migration runner support.
- `/backend/src/jobs/` — background worker(s), especially embedding pipeline worker.
- `/backend/src/providers/` — external provider adapters (AI + transcript provider).
- `/backend/src/middleware/` — request middleware (rate limiting, request IDs).
- `/backend/src/services/` — service-layer orchestration utilities.
- `/backend/db/migrations/` — SQL migrations for schema evolution.

### `/src/`
Modern admin/front-end application modules and services.

Key subdirectories:
- `/src/admin/` — admin shell, screen routing, and admin context.
- `/src/services/` — frontend API client modules.
- `/src/hooks/` — reusable frontend hooks.

### `/components/`
Shared React UI views/components (dashboard, sources, governance, ask, settings, analytics, etc.).

### `/docs/`
Project documentation set (requirements, architecture, roadmap, readiness, specs).

### `/wordpress-connector/`
WordPress plugin/connector assets and PHP integration code for ingestion/sync-related workflows.

### `/docker/` and `docker-compose.yml`
Containerized local infrastructure support (notably PostgreSQL + extension initialization).

### `/scripts/`
Root-level runtime orchestration/helper scripts for local development.

## Module Organization Pattern
- **API-first backend segmentation** by route domain and admin/public boundaries.
- **Repository pattern** for SQL persistence operations.
- **Core-domain modules** for AI pipeline stages.
- **UI module grouping** by product area (sources, knowledge, analytics, ask, settings).
- **Connector isolation** for CMS-side integration assets.

## Notable Structural Characteristics
- Mixed legacy/new frontend organization exists (`components/` plus `src/admin/...`) while remaining functionally integrated.
- Architecture balances implemented direct paths (SQL + pgvector retrieval) with abstraction modules intended for broader provider pluggability.
