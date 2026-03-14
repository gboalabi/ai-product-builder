# DICOS Repository Structure

## Monorepo Layout Overview
DICOS is organized as a multi-application monorepo with shared packages and centralized docs/infra.

## Major Directories

### `apps/`
Contains runnable applications.
- `apps/web`: primary Next.js SaaS frontend
- `apps/api`: Node/Express REST API and orchestration services
- `apps/worker`: asynchronous queue worker for generation execution
- `apps/web-legacy`: preserved legacy UI reference implementation

### `packages/`
Contains shared libraries and domain modules.
- `packages/db`: Prisma schema, migrations, seed/backfill scripts
- `packages/queue`: queue contracts and queue setup
- `packages/compliance`: compliance evaluation engine
- `packages/models`: model/provider abstraction and routing helpers
- `packages/ai`: AI-related abstractions/utilities
- `packages/dip-engine`: DIP/domain intelligence helpers
- `packages/domain`: shared domain-level constructs
- `packages/observability`: logging/observability helpers

### `docs/`
Canonical architecture, roadmap, implementation, and development-log documentation.
- phase specs and implementation plans
- system/architecture references
- parity/audit and launch-tracking documents

### `infra/`
Infrastructure definitions for local/runtime dependencies (e.g., compose-based services).

### `scripts/`
Verification and smoke-test scripts for API, worker, and pipeline reliability checks.

### `backups/`
Database backup artifacts used for recovery/reference workflows.

## Module Organization Pattern
- **App-level code** handles runtime entrypoints, route/UI composition, and integration wiring.
- **Package-level code** encapsulates reusable business logic, contracts, and shared infrastructure access.
- **Docs-first governance** keeps planning/status and verification evidence alongside implementation.

## Organizational Intent
The structure separates concerns cleanly:
- product interfaces in `apps/*`
- reusable platform logic in `packages/*`
- operational guidance in `docs/*`
- runtime support in `infra/*`
- verification tooling in `scripts/*`
