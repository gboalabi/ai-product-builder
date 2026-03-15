# IKIRA AI Studio — Repository Structure

## Repository Organization Summary
The repository is organized as a full-stack TypeScript application with clear separation between frontend UI modules, backend API/services, shared types, and product documentation.

## Major Directories and Purpose

### `/components`
Reusable UI components, including layout, common UI primitives, and feature-specific widgets.

### `/pages`
Route-level frontend modules representing major product surfaces (generation flows, library, projects, admin, settings, help, storyboard pages).

### `/context`
React context providers for global client concerns (theme, chat widget, image session state).

### `/hooks`
Custom React hooks used by frontend modules.

### `/services` (frontend/domain services)
Client-side service layer that orchestrates API calls, feature logic, and domain-specific workflows (images, assets, projects, storyboard, admin settings, utilities).

### `/server`
Backend application code (Express entrypoints, route modules, config, provider adapters, persistence services, utility helpers).

Key backend sub-areas:
- `/server/routes`: API route grouping by domain (generation, assets, projects, admin, storyboard)
- `/server/services`: provider integrations, adapters, and data services
- `/server/models`: internal model registries/mappings
- `/server/config`: runtime flags and environment behavior
- `/server/utils`: low-level helper utilities

### `/docs`
Product and engineering documentation (requirements, app flow, architecture, roadmap, integration notes).

### Worker/Integration Folders
Dedicated worker/integration directories support GPU/serverless processing experiments and deployments for specific AI pipelines.

## How Modules Are Organized
- **UI modules** are grouped by route and feature area.
- **Business/domain logic** is separated into service layers.
- **Backend API boundaries** are split by domain route groups.
- **Provider-specific logic** is isolated in adapter-style backend services.
- **Shared contracts/types** support consistent request/response behavior across layers.

## Separation Between Application Layers
- **Presentation Layer (Frontend):** Rendering, user interaction, local session/state management
- **Application Layer (Frontend Services + Backend Routes):** Use-case orchestration and request handling
- **Integration Layer (Backend Adapters):** External AI provider communication and normalization
- **Data/Persistence Layer (Backend Stores):** Asset/project/storyboard metadata and retrieval logic

This structure supports modular growth while keeping implementation concerns separated and easier to maintain.
