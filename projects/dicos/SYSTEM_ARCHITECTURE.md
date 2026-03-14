# DICOS System Architecture

## Architectural Style
DICOS follows a layered, service-oriented architecture in a monorepo:
- Presentation layer (web app)
- API layer (REST services + middleware)
- AI orchestration layer (pipeline execution and control)
- Domain intelligence layer (DIP rules/templates/context)
- Data/infra layer (database, queue, storage, observability)

## Major System Components
- **Web application (`apps/web`)**: tenant/workspace-aware SaaS UI and orchestration views
- **API service (`apps/api`)**: authenticated, tenant-scoped REST interface and business services
- **Worker service (`apps/worker`)**: asynchronous pipeline execution via queue consumers
- **Shared packages (`packages/*`)**: compliance logic, model/provider abstractions, queue, database schema/client, domain helpers, observability utilities
- **Infrastructure (`infra/`)**: local compose setup for Postgres, Redis, and object-storage-compatible service

## Frontend Structure
- Next.js application with app-shell patterns for dashboard, DIPs, content packs, analytics, compliance, team, settings, and orchestration
- Role-based UI gating for Owner/Admin/Editor/Viewer behaviors
- Workspace/tenant context with branding-aware UI behavior
- Polling/state integration for run progress and outputs

## Backend Structure
- Express-based API with middleware layers for:
  - request context and logging
  - auth enforcement
  - tenant resolution/scoping
  - RBAC checks
  - rate limiting
  - audit logging
- Route groups include auth/session, DIPs, documents/rules/templates, generation runs, content packs, and system health
- Service modules implement pipeline orchestration, model invocation, budget checks, validation, and retrieval logic

## Orchestration Layers
- Run creation enqueues jobs to a generation queue
- Worker claims and processes queued runs with deterministic state transitions
- Step-level lifecycle includes context retrieval, prompt build, model routing, budget check, invocation, output validation, compliance evaluation, and persistence
- Retry/regeneration controls enforce eligibility and depth limits

## AI Pipeline Components
- Prompt builder
- Model routing/policy logic
- Budget preflight controller
- Provider invocation abstraction
- Structured output validator
- Compliance/rule evaluation
- Token/cost accounting and run diagnostics persistence

## Data Storage Approach
- **Primary DB**: PostgreSQL (with pgvector support for embedding use cases)
- **Queue backend**: Redis + BullMQ for asynchronous processing
- **Object storage pattern**: S3-compatible approach (local dev via MinIO pattern)
- **Relational model coverage**:
  - tenancy/users/subscriptions
  - DIP profiles/versions/rules/templates/documents/chunks
  - content packs/items
  - generation runs/steps/outputs/token usage/cost snapshots
  - compliance flags, assets, audit logs

## External Integrations (High Level)
- LLM provider integration through provider abstraction packages
- Authentication provider integration pattern (implemented with environment-driven auth strategy)
- Infrastructure services (database, cache/queue, object storage)

> Security Note: This overview intentionally excludes secrets, credentials, and internal/private endpoint details.
