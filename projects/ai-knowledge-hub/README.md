# AI Knowledge Hub — Repository Audit (Portfolio Overview)

This audit package provides a non-sensitive, implementation-informed overview of the **AI Knowledge Hub** codebase. It is designed for external readers (recruiters, stakeholders, documentation consumers) and intentionally avoids exposing proprietary source files.

## System Purpose
AI Knowledge Hub is a multi-tenant platform that ingests organizational knowledge, indexes it for semantic retrieval, and generates grounded AI answers with citations and role-aware scope controls.

## Core Capabilities
- Multi-tenant ingestion and indexing workflows
- Vector-backed retrieval and grounded answer generation
- Scope-aware access filtering (`public/member/staff`)
- Citation-rich Ask Hub response flow (including video timestamp support)
- Admin operations for sources, knowledge visibility, and usage analytics

## Architecture Summary
- **Frontend:** React admin/query experience with routed product modules
- **Backend:** Express + TypeScript API with modular route/service/repository layers
- **Data:** PostgreSQL + pgvector for transactional + semantic retrieval storage
- **AI Pipeline:** ingestion → chunking → embedding worker → retrieval → grounded generation

## Implementation Status Snapshot
- Core platform, ingestion, retrieval, worker processing, and baseline analytics are implemented.
- Governance depth, connector breadth, and advanced analytics remain partially implemented.
- Estimated overall completion is approximately **77%** (late MVP / pre-production hardening stage).

## Documentation Links
- [PROJECT_OVERVIEW.md](./PROJECT_OVERVIEW.md)
- [SYSTEM_ARCHITECTURE.md](./SYSTEM_ARCHITECTURE.md)
- [PRODUCT_CAPABILITIES.md](./PRODUCT_CAPABILITIES.md)
- [IMPLEMENTATION_STATUS.md](./IMPLEMENTATION_STATUS.md)
- [PROJECT_COMPLETION_ESTIMATE.md](./PROJECT_COMPLETION_ESTIMATE.md)
- [DEVELOPMENT_WORKFLOW.md](./DEVELOPMENT_WORKFLOW.md)
- [REPO_STRUCTURE.md](./REPO_STRUCTURE.md)
- [ARCHITECTURE_OVERVIEW_FOR_EXTERNAL.md](./ARCHITECTURE_OVERVIEW_FOR_EXTERNAL.md)
