# DICOS Project Overview

## Project Name
**DICOS (Domain Intelligence Content Operating System)**

## Purpose
DICOS is a multi-tenant SaaS platform for generating domain-aware, policy-constrained content across multiple channels from a single source input.

## Problem It Solves
Organizations often struggle to produce consistent, compliant, high-quality content quickly across channels (blog, social, newsletter, announcements, etc.). DICOS addresses this by combining reusable domain intelligence with AI orchestration and governance controls.

## Target Users
- Content teams in regulated or policy-sensitive domains
- Marketing and operations teams managing multi-channel output
- Tenant/workspace administrators overseeing governance and branding
- Internal operators monitoring generation runs and system health

## Key Capabilities
- Multi-tenant workspace model with role-based access controls
- Domain Intelligence Packs (DIPs) for rules, templates, and context
- AI generation pipeline with budget checks, validation, retry/regen controls, and run lifecycle tracking
- Content pack workflow for structured multi-channel output generation
- Operational visibility via orchestration views and system health surfaces

## Current Maturity Level
**Late implementation / pre-hardening maturity**

Based on repository planning and development logs:
- Core data layer, DIP engine, orchestration pipeline, worker processing, and major UI surfaces are implemented
- End-to-end reliability hardening and later roadmap phases (admin expansion, enterprise features, marketplace/plugins) remain in progress or planned

## High-Level System Operation
1. A tenant-scoped user initiates content generation (typically as part of a content pack workflow).
2. The API creates and queues a generation run.
3. A worker processes the run through orchestrated steps (context retrieval, prompt build, model routing, budget check, invocation, validation, compliance evaluation, persistence).
4. Outputs, run states, step telemetry, token/cost usage, and diagnostics are stored.
5. The web app surfaces run progress, outputs, status, and operational health for users and operators.
