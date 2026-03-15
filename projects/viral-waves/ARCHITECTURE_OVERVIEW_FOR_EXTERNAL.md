# Architecture Overview (External-Friendly)

Viral Waves is a trend intelligence platform that combines data analysis and AI guidance in a single workflow.

At a high level, the system has three layers:
1. **Frontend application** where users discover trends, open strategy recommendations, and manage planning workflows.
2. **Backend API service** that serves trend data, stores user workflow artifacts (watchlists/planner drafts), and manages alert logic.
3. **Data + AI layer** where trend signals are stored and scored in a database, while AI generates execution guidance for selected opportunities.

## Simplified Flow
1. Trend signals are collected and processed into ranked daily outputs.
2. The backend exposes those ranked signals to the frontend dashboards.
3. Users select a trend and request AI-generated strategy recommendations.
4. Users can save signals, configure alerts, and persist campaign drafts for follow-through.

## Why This Architecture Matters
- **Data-backed discovery:** trend ranking is grounded in stored signal data.
- **Actionability:** AI helps translate trend detection into content strategy.
- **Workflow continuity:** planner/watchlist/alerts help teams move from insight to execution.

## Current Position
The architecture is a strong MVP-to-early-production foundation. Core data, API, and UI workflows are implemented, with future expansion expected around deeper agency operations, automation infrastructure, and enterprise platform controls.
