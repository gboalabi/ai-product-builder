# Product Capabilities

## Core Platform Capabilities
- **Trend signal discovery:** surfaces top-ranked acceleration-stage entities from stored scoring outputs
- **Strategy generation:** produces AI creative briefs (hook/script/audio/style/hashtags) for selected trends
- **Watchlist management:** save and remove monitored trends by entity and region
- **Planner workflow foundation:** convert discovered trends into persisted campaign drafts
- **Alerting foundation:** create threshold rules and evaluate/record trigger events

## Key Workflows
1. **Discover:** user loads ranked trend signals and reviews score/momentum context.
2. **Analyze:** user opens Action Strategy for a selected signal.
3. **Plan:** user saves strategy output as a planner draft with immutable signal snapshot metadata.
4. **Monitor:** user saves trends to watchlist and configures acceleration threshold alerts.

## Generation Process
- Trend strategy generation is LLM-backed and schema-constrained.
- Trend ranking itself is data-backed from stored pipeline outputs (not exclusively LLM-generated).
- System currently supports both DB-ranked trend feeds and an AI-generated trend endpoint path.

## Governance Features
- Immutable planner snapshot field protections during update operations
- Input validation and typed payload expectations across primary APIs
- Retry/timeout wrappers for AI requests
- Additive migration and roadmap/documentation governance process in repo docs

## Analytics Features
- Viral score and confidence score surfaces
- Velocity/acceleration-related trend context
- Rank movement snapshots (today/yesterday/day-2 deltas) stored with planner drafts
- Basic growth direction indicators in trend presentation

## Major Product Modules
- **Trend Pulse (Discover)**
- **Strategy Modal (AI brief generation)**
- **Planner Dashboard (draft lifecycle + alert settings)**
- **Agency Hub (portfolio-style dashboard UI foundation)**
