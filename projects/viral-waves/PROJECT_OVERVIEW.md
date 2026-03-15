# Viral Waves — Project Overview

## Project Name
**Viral Waves (Trend Predictor / AI Trend Intelligence Platform)**

## Purpose
Viral Waves is a trend intelligence platform focused on identifying early social momentum signals (currently centered on TikTok trend entities), then helping creators and marketing teams act on those signals with AI-assisted campaign strategy.

## Problem It Solves
Teams often detect trends too late, after competition and saturation reduce upside. Viral Waves addresses this by combining:
- data-backed ranking of emerging signals,
- momentum interpretation (velocity/acceleration context), and
- fast strategy generation for execution.

## Target Users
- Individual creators seeking early trend opportunities
- Agency planners managing multiple campaigns/clients
- Growth teams that need signal monitoring + draftable creative recommendations

## Key Capabilities (Current)
- DB-backed trend signal feed (ranked daily)
- Trend watchlist save/unsave
- Threshold-based alert rule creation and event logging
- Planner draft creation and lifecycle management (draft/approved/archived)
- AI-generated strategy briefs for selected trends
- CLI ingestion and scoring pipeline support for trend data operations

## Current Maturity Level
**Early production foundation / late MVP-integration stage**

The repository goes beyond prototype UI. Core backend APIs, persistence, migration-based schema evolution, and scoring stages exist. Some areas remain partial (notably generalized provider adapters, deeper agency workflows, auth/billing, and automated background worker infrastructure).

## How the System Works (Summary)
1. External trend signals are ingested via CLI ingestion scripts into PostgreSQL.
2. Scoring stages compute ranked daily trend outputs (raw → scored → velocity → acceleration).
3. Backend API serves ranked trends and enriches them with movement/alert context.
4. Frontend displays discover/planner/agency views and lets users save signals and manage planner drafts.
5. Strategy generation uses an LLM service to create actionable creative guidance from selected trends.
