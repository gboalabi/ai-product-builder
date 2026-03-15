# IKIRA AI Studio — Project Overview

## Project Name
IKIRA AI Studio

## Project Purpose
IKIRA AI Studio is a unified AI creative platform designed to help users generate, iterate on, and organize creative assets in one workspace instead of using disconnected tools.

## Problem the System Solves
Creative teams often juggle separate products for image generation, editing, asset organization, and project planning. This creates workflow fragmentation, repeated context switching, and weak continuity between ideation and production. IKIRA addresses this by combining generation, curation, and project-oriented creative workflows in one system.

## Target Users
- Individual creators (designers, writers, marketers, filmmakers)
- Small creative teams and founders
- Power users who need multi-model AI creation workflows
- Internal/admin operators who manage model access and platform behavior

## Core Product Idea
Provide a "creative operating system" that connects AI generation pipelines with a persistent asset library, project grouping, and storyboard workflows so users can move from idea to organized output with minimal friction.

## Key Capabilities
- Multi-route generation experience (images today, with video/script/audio pathways defined)
- Reference-guided and prompt-driven image workflows
- Model/pipeline selection with capability-aware behavior
- Asset library management and project assignment
- Storyboard creation and scene-based creative planning
- Admin-controlled feature gating and quality controls
- Mock and real-provider execution modes for development and rollout safety

## Current Maturity Level
The product is in an advanced pre-beta stage for image-centric workflows. Core image generation, library/projects persistence, and storyboard foundations are implemented. Additional modules (video, script, audio, full auth/credits, expanded admin analytics) are planned or partially staged according to roadmap phases.

## Summary of How the System Works
Users interact with a React-based studio interface and navigate modular workflows (Generate, Library, Projects, Storyboard, Admin, etc.). Generation requests are sent to a backend API that routes requests through provider adapters and pipeline logic, then normalizes results into a consistent application format. Generated outputs can be persisted as assets, organized into projects, and reused in iterative creative workflows.