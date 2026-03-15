# AI Knowledge Hub — Product Capabilities

## Core Platform Capabilities
- **Tenant-isolated knowledge operations** across ingestion, indexing, retrieval, and analytics.
- **Grounded Q&A experience** with source-linked citations.
- **Role/scope-aware response control** (`public`, `member`, `staff`) enforced before answer generation.
- **Operational source management** for sync state, counts, and lifecycle actions.
- **Admin analytics visibility** for usage and source impact.

## Key Workflows
1. **Content Ingestion Workflow**
   - Source data is submitted through ingestion endpoints.
   - Documents are upserted, chunked, and queued for embeddings.
   - Source registry stats and sync timestamps are updated.

2. **Ask Hub Query Workflow**
   - User submits question with site + instance context.
   - Retrieval returns top candidate chunks.
   - Visibility constraints remove unauthorized chunks.
   - Grounded answer is generated from allowed context.
   - Response includes confidence and citations.

3. **Admin Operations Workflow**
   - Admin views source/document/chunk health.
   - Admin reviews dashboard metrics and top sources.
   - Admin applies settings and stabilization actions.

## Generation Process (Answer Pipeline)
- Input validation and scope checks.
- Semantic retrieval from vectorized chunk corpus.
- Governance/visibility filtering.
- Grounded prompt assembly.
- Model invocation (Gemini adapter).
- Response shaping with status, confidence, scope badge, and citation metadata.
- Usage + query log recording.

## Governance Features
- Instance-type visibility ladder (`public/member/staff`).
- Pre-generation retrieval filtering to prevent restricted-source leakage.
- Source metadata/citation visibility signaling in response payloads.
- Admin-facing governance modules and topic/governance API surfaces (mixed maturity across features).

## Analytics Features
- Query logging with answer status and citation summaries.
- Dashboard overview metrics (sources, documents, chunks, queries).
- Query trend aggregation (recent time-windowed activity).
- Top cited sources from historical logs.
- Workspace usage counters for operational monitoring.

## Major Product Modules
- **Dashboard** — system and activity overview.
- **Sources** — connector visibility, sync lifecycle, ingestion transparency.
- **Knowledge** — indexed corpus browse/filter/reindex operations.
- **Topics & Governance** — policy-oriented management surfaces.
- **Analytics** — usage and citation-driven metrics.
- **Ask Hub** — scoped, citation-backed answer interface.
- **Settings/Stabilization** — workspace controls and reset/audit utilities.
