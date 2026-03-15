# IKIRA AI Studio — System Architecture

## Architecture Summary
IKIRA AI Studio follows a layered web architecture with a React frontend, an Express backend API, provider adapters for AI services, and persistence services for assets/projects/storyboards. The system is designed to keep provider-specific logic isolated from UI workflows.

## Major System Components
- **Web Client (Frontend):** User-facing studio experience, route-based modules, session/state orchestration
- **Backend API:** Request validation, pipeline routing, provider abstraction, result normalization
- **AI Provider Adapter Layer:** Integration boundary for multiple generation providers and models
- **Persistence Layer:** Asset/project/storyboard storage services and metadata handling
- **Admin Configuration Layer:** Feature gating, pipeline enablement, and operational controls

## Frontend Structure
- **Framework:** React + TypeScript with router-driven page modules
- **Layout:** Shared shell (header/sidebar/layout) with feature pages (Generate, Library, Projects, Storyboard, Admin)
- **State & Context:** Context providers for theme, chat widget, and image-session continuity
- **Service Interfaces:** Frontend service modules call backend APIs through stable contracts
- **Capability-Driven UI:** Pipeline registry and capability metadata control available inputs and behaviors

## Backend Structure
- **Core Server:** Express application with modular route registration
- **Route Modules:** Separate route groups for generation, admin, assets, projects, and storyboard workflows
- **Service Modules:** Domain services for image generation, provider calls, normalization, and persistence
- **Environment Strategy:** Backend-only configuration for provider credentials, with mock mode support for local/testing paths

## Orchestration Layers
- **Request Routing:** Frontend sends generic generation intent; backend selects appropriate pipeline behavior
- **Validation & Guardrails:** Input validation, reference limits, and route-level constraints
- **Pipeline Selection:** Prompt-only vs reference-guided flows routed to different provider adapters
- **Normalization:** Diverse provider outputs transformed into a consistent response shape expected by the UI

## AI Pipeline Components
- **Prompt-Only Generation Pipelines:** Text-driven image generation paths
- **Reference-Guided Pipelines:** Edit or guidance paths using uploaded references
- **Mock Providers:** Deterministic development/testing behavior without live provider dependencies
- **Provider Adapters:** Encapsulate external API schemas to keep core app contracts stable

## Data Storage Approach
- **Application Metadata:** Stored as lightweight JSON-backed stores/services in current implementation
- **Generated Asset Records:** Saved with metadata such as prompt, pipeline, size, and timestamps
- **Project Associations:** Assets can be grouped/assigned to project entities
- **Storyboard Data:** Storyboard projects, scenes, and anchor context stored through dedicated storyboard services

## External Integrations
- Multiple AI model/provider integrations through backend adapters
- Google AI ecosystem usage for specific generation/intelligence pathways
- Additional provider integrations for advanced image pipelines
- Optional GPU/serverless execution paths abstracted behind backend services

All integrations are handled server-side to avoid exposing sensitive credentials in the client.

## High-Level Data Flow
1. User creates a request in the frontend (prompt, optional references, selected pipeline/model context).
2. Frontend service sends a normalized request to backend API routes.
3. Backend validates request and applies feature/pipeline rules.
4. Backend dispatches to the appropriate provider adapter (or mock path).
5. Provider response is normalized into a standard generation result structure.
6. Frontend receives results, updates session gallery, and optionally persists assets to library/projects.
7. Metadata and associations are available for downstream organization and reuse workflows.
