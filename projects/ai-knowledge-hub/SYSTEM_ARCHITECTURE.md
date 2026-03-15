# AI Knowledge Hub — System Architecture

## Architecture Style
The implemented system follows a **modular monolith + background worker** pattern:
- React frontend (admin/query experience)
- Express API backend (business logic, ingestion, retrieval, governance enforcement)
- PostgreSQL + pgvector for transactional and vector data
- In-process worker loop for embedding/backfill jobs

## Major System Components
1. **Frontend UI Layer**
   - Admin shell and module screens (dashboard, sources, knowledge, governance, analytics, settings, Ask Hub).
   - API client layer for tenant-scoped admin and query requests.
2. **Backend API Layer**
   - Public API routes (`/api/query`, `/api/ingest`, `/api/retrieve`, `/api/sources`, `/api/health`).
   - Admin API namespace (`/api/admin/...`) for operational controls and dashboards.
3. **Core Domain Services**
   - Ingestion, chunking, embeddings, retrieval, answer prompt orchestration, citation shaping.
4. **Persistence Layer**
   - Repository modules for documents, chunks, sources registry, jobs, settings, usage, logs.
5. **Background Processing**
   - Embedding worker that polls pending jobs, backfills chunking for stored docs, and writes vectors.
6. **Provider Adapters**
   - Gemini AI provider adapter for text generation + embeddings.
   - Video transcript provider adapter (implemented Vimeo path, extensible provider contract).

## Frontend Structure
- Root React app + admin route shell.
- Screen-level modules under admin for domain areas.
- Shared component layer for views/cards and Ask Hub interaction UX.
- Service helpers for API communication (`adminApi`, `askHubApi`).

Design emphasis: frontend remains orchestration/presentation heavy, while security and retrieval logic stay backend-side.

## Backend Structure
- **Server bootstrap:** DB bootstrap, middleware setup, router mount, error discipline.
- **Middleware:** request IDs + rate limiting for high-risk public query/retrieve routes.
- **Route handlers:** input validation, tenant/scope handling, orchestration with core services.
- **Core modules:** chunking, retrieval ranking, grounded prompt creation, embedding operations.
- **DB repos:** encapsulated SQL for operational entities.

## Orchestration Layers
- API orchestration combines:
  - request validation
  - tenant/scope constraints
  - retrieval + visibility filtering
  - model invocation
  - usage/log persistence
- Ingestion orchestration combines:
  - tenant upsert
  - document upsert/hash checks
  - chunk lifecycle updates
  - embedding job queue management
  - source registry sync

## AI Pipeline Components
1. **Ingestion**: raw content arrives from source connectors/endpoints.
2. **Normalization/Chunking**: content split into retrieval units (including transcript-aware chunk windows).
3. **Embedding Queue**: jobs inserted per document/chunk set.
4. **Worker Processing**: embeddings generated through Gemini adapter.
5. **Vector Retrieval**: pgvector similarity search (tenant-scoped, active chunk constrained).
6. **Governance Filter**: instance-type visibility ladder (`public/member/staff`) applied pre-answer.
7. **Grounded Generation**: prompt built from permitted chunks; limited response if grounding insufficient.
8. **Citation Packaging**: source metadata and optional timestamps included in response.

## Data Storage Approach
- **Primary DB:** PostgreSQL.
- **Vector Storage:** pgvector column in `chunks` table.
- **Core entities:** tenants, documents, chunks, embedding_jobs.
- **Operational entities:** sources_registry, workspace_settings, workspace_usage, query_logs, admin audit/lifecycle tables.
- **Indexing:** a mix of relational indexes and ivfflat vector index for retrieval performance.

## External Integrations
- **Gemini (Google GenAI):** generation + embedding model calls.
- **WordPress connector path:** ingestion of website-originated documents.
- **Vimeo API path:** transcript fetch support through tokenized provider adapter.

Security note: this report intentionally omits credentials, environment secret values, and private runtime endpoint details.
