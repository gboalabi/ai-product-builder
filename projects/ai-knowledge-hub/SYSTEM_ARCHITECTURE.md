# AI Knowledge Hub — System Architecture

## Architecture Style

The system follows a **modular monolith + background worker architecture** designed for production AI knowledge systems.

Core design principles:

- Clear separation between UI, API, AI pipeline, and storage layers
- Tenant-isolated retrieval pipelines
- Background processing for embedding and ingestion workloads
- Vector-based semantic retrieval backed by PostgreSQL + pgvector

Primary components:

- React frontend (admin UI + Ask Hub interface)
- Express API backend (business logic, ingestion, retrieval, governance)
- PostgreSQL + pgvector (transactional + vector storage)
- Background worker loop (embedding + document processing)
- Gemini AI provider integration (generation + embeddings)

---

# High-Level System Architecture

User / Admin
    │
    ▼
React Frontend (Admin UI + Ask Hub)
    │
    ▼
Express API Layer
  ├ Query API
  ├ Ingestion API
  ├ Retrieval API
  └ Admin APIs
    │
    ▼
Core AI Services
  ├ Ingestion Service
  ├ Chunking Service
  ├ Retrieval Engine
  ├ Prompt Orchestrator
  └ Citation Builder
    │
    ▼
Persistence Layer
  ├ PostgreSQL (documents, tenants, jobs)
  └ pgvector (semantic chunk embeddings)
    │
    ▼
Background Worker
  └ Embedding generation + chunk backfill
    │
    ▼
Gemini AI Provider
  ├ Embeddings
  └ Answer generation

---

# Major System Components

## 1. Frontend UI Layer

The frontend provides the administrative and user interaction interface for the platform.

Key responsibilities:

- Admin shell and module screens:
  - dashboard
  - sources
  - knowledge
  - governance
  - analytics
  - settings
  - Ask Hub
- Query interface for knowledge retrieval
- Citation rendering and answer history
- API client layer for tenant-scoped operations

Design emphasis:

The frontend focuses on presentation and orchestration, while security, retrieval, and governance logic remain on the backend.

---

## 2. Backend API Layer

The Express backend acts as the central orchestration layer for the platform.

Public routes include:

- `/api/query`
- `/api/ingest`
- `/api/retrieve`
- `/api/sources`
- `/api/health`

Administrative routes:

- `/api/admin/...`

Responsibilities:

- request validation
- tenant scoping
- governance enforcement
- AI pipeline orchestration
- logging and analytics capture

---

## 3. Core Domain Services

The core service layer encapsulates the AI knowledge system logic.

Key services include:

- ingestion pipeline orchestration
- document normalization and chunking
- embedding creation
- retrieval ranking
- prompt grounding
- answer generation orchestration
- citation formatting

This layer ensures LLM responses are grounded in retrieved knowledge chunks.

---

## 4. Persistence Layer

The system uses PostgreSQL as the primary data store.

Primary database:
PostgreSQL

Vector storage:
pgvector extension stored in the `chunks` table.

Core entities:

- tenants
- documents
- chunks
- embedding_jobs

Operational entities:

- sources_registry
- workspace_settings
- workspace_usage
- query_logs
- admin audit tables
- connector lifecycle tables

Indexing strategy:

- relational indexes for operational queries
- ivfflat vector index for semantic retrieval

---

## 5. Background Processing

A background worker performs asynchronous processing tasks.

Responsibilities include:

- polling embedding job queue
- chunk backfilling for existing documents
- generating embeddings
- updating document and job lifecycle states

This architecture prevents expensive embedding tasks from blocking API requests.

---

## 6. Provider Adapters

External AI services are integrated through provider adapters.

Implemented adapters:

Gemini AI Provider

Used for:

- embedding generation
- answer generation

Video Transcript Provider

Implemented path:

- Vimeo transcript ingestion

The provider adapter model allows additional connectors to be integrated without modifying core services.

---

# Frontend Structure

Frontend implementation uses a modular React architecture.

Structure:

- root React application
- routed admin shell
- module-based screens for each domain area
- shared component library
- Ask Hub interaction components
- API service helpers (`adminApi`, `askHubApi`)

Key design goal:

Keep business logic on the backend while the frontend handles interaction and state orchestration.

---

# Backend Structure

The backend follows a layered service architecture.

Server bootstrap:

- database initialization
- middleware registration
- router mounting
- centralized error handling

Middleware:

- request ID tracing
- rate limiting
- query endpoint protection

Route handlers:

- request validation
- tenant context extraction
- orchestration with core services

Core modules:

- chunking engine
- retrieval ranking
- prompt construction
- embedding operations

Database repositories encapsulate SQL access for:

- documents
- chunks
- sources
- jobs
- usage
- logs

---

# Orchestration Layers

## Query Orchestration

Query execution pipeline:

1. request validation  
2. tenant context resolution  
3. visibility filtering  
4. semantic retrieval  
5. prompt construction  
6. LLM invocation  
7. usage tracking  
8. query logging  
9. citation packaging  

---

## Ingestion Orchestration

Ingestion pipeline includes:

1. tenant upsert  
2. document upsert and hash comparison  
3. chunk lifecycle updates  
4. embedding job creation  
5. source registry synchronization  

This design ensures idempotent ingestion and consistent embedding lifecycle management.

---

# AI Pipeline Components

The AI pipeline implements a retrieval-augmented generation (RAG) architecture.

1. Ingestion  
Content arrives from external connectors or ingestion endpoints.

2. Normalization / Chunking  
Documents are split into retrieval units. Transcript sources use timestamp-aware chunk windows.

3. Embedding Queue  
Embedding jobs are created per document or chunk set.

4. Worker Processing  
Embeddings are generated through the Gemini provider adapter.

5. Vector Retrieval  
pgvector similarity search is executed against active chunks with tenant-level isolation.

6. Governance Filtering  
Access rules are enforced using a visibility ladder:

- public
- member
- staff

7. Grounded Generation  
Prompts are constructed from retrieved knowledge chunks. If insufficient grounding exists, a limited knowledge response is returned.

8. Citation Packaging  
Responses include document metadata, source identifiers, and optional timestamp links for video transcripts.

---

# Data Storage Approach

Primary datastore:
PostgreSQL

Vector storage:
pgvector

Benefits:

- unified transactional + vector storage
- simpler operational model
- strong relational constraints
- efficient semantic search

---

# External Integrations

Gemini (Google GenAI)

Used for:

- embedding generation
- answer generation

WordPress Connector

Supports ingestion of:

- website documents
- structured content

Vimeo API

Used for:

- transcript ingestion
- timestamp-linked citation generation

---

# Security Note

This architecture report intentionally omits:

- credentials
- environment variables
- secret values
- internal runtime endpoints
- private infrastructure configuration

The document provides implementation-informed architecture insight without exposing sensitive system details.
