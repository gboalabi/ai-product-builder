# Viral Waves — Repository Audit Report

This folder contains a code-grounded audit summary of the Viral Waves private repository. The reports are designed for portfolio and architecture review use without exposing proprietary source code.

## System Purpose
Viral Waves is a trend intelligence platform that identifies emerging social signals, ranks them with a data-backed pipeline, and helps teams operationalize those insights through AI-assisted strategy generation and planner workflows.

## Core Capabilities
- Ranked trend signal discovery from persisted scoring outputs
- AI-generated strategy briefs for selected trends
- Planner draft lifecycle management with immutable signal snapshots
- Watchlist persistence and threshold-based alert rule/event tracking
- CLI ingestion + scoring pipeline operations

## Architecture Summary
- **Frontend:** React dashboards (Discover, Planner, Agency)
- **Backend:** Express API for trends, strategy, planner, watchlist, and alerts
- **Data layer:** PostgreSQL with migration-based schema evolution
- **Pipeline:** Script-driven ingestion/import and multi-stage scoring
- **AI layer:** Gemini workflows for strategy and trend generation paths

## Implementation Status (High-Level)
- Strong MVP foundation is implemented across API, persistence, and core workflows.
- Product and platform depth is partial in some areas (agency operations, automation workers).
- Auth/billing and broader commercialization controls remain planned.

## Documentation Index
- [PROJECT_OVERVIEW.md](./PROJECT_OVERVIEW.md)
- [SYSTEM_ARCHITECTURE.md](./SYSTEM_ARCHITECTURE.md)
- [PRODUCT_CAPABILITIES.md](./PRODUCT_CAPABILITIES.md)
- [IMPLEMENTATION_STATUS.md](./IMPLEMENTATION_STATUS.md)
- [PROJECT_COMPLETION_ESTIMATE.md](./PROJECT_COMPLETION_ESTIMATE.md)
- [DEVELOPMENT_WORKFLOW.md](./DEVELOPMENT_WORKFLOW.md)
- [REPO_STRUCTURE.md](./REPO_STRUCTURE.md)
- [ARCHITECTURE_OVERVIEW_FOR_EXTERNAL.md](./ARCHITECTURE_OVERVIEW_FOR_EXTERNAL.md)
