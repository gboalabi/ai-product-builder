# AI Knowledge Hub — Project Overview

## Project Name
**AI Knowledge Hub**

## Purpose
AI Knowledge Hub is a multi-tenant knowledge platform that ingests organizational content, indexes it for retrieval, and delivers grounded AI answers with citations through a web-based admin and query experience.

## Problem It Solves
- Reduces fragmented knowledge spread across CMS pages, documents, and media systems.
- Improves trust in AI responses by grounding output in indexed source content.
- Enforces role-aware visibility so restricted information is not exposed in responses.
- Gives administrators operational control over ingestion, source health, and usage insight.

## Target Users
- **Admins / Operators:** manage sources, ingestion state, settings, and observability.
- **Staff / Member / Public audiences:** receive scoped answers based on access level.
- **Organizations running multiple properties:** use tenant isolation for data separation.

## Key Capabilities
- Multi-tenant architecture with tenant-scoped data and queries.
- Source ingestion for WordPress and video transcripts (Vimeo-focused provider path).
- Chunking + embedding pipeline with background worker processing.
- pgvector-backed semantic retrieval with governance-aware filtering.
- Grounded answer generation via Gemini provider integration.
- Citation rendering with timestamp-aware links for video-derived chunks.
- Admin metrics and query logging for operational visibility.

## Current Maturity Level
**Late MVP / pre-production hardening stage.**

The repository shows substantial implemented functionality across ingestion, retrieval, worker processing, admin APIs, and frontend workflows. Some subsystems remain partial or planned (e.g., deeper governance tooling, additional connectors, expanded analytics/exports).

## Summary of How the System Works
1. External content is ingested into tenant-scoped documents.
2. Content is normalized/chunked and queued for embedding.
3. Background workers generate embeddings and persist vectors in PostgreSQL (pgvector).
4. Query requests retrieve top semantic chunks, then apply role/scope visibility constraints.
5. A grounded prompt is assembled from permitted chunks and sent to the AI provider.
6. The response returns with confidence level, scope badge, and citations (including optional video timestamps).
7. Usage and query logs are recorded for analytics and admin dashboards.
