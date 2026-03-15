# IKIRA AI Studio — Architecture Overview (External Audience)

## What the System Is
IKIRA AI Studio is a full-stack creative AI platform that helps users generate visual content, organize outputs, and manage creative workflows in one product experience. It combines a modern web interface with a backend orchestration layer that connects to multiple AI generation providers.

## High-Level Architecture Layers

### 1) Experience Layer (Frontend)
The web app provides the studio interface where users create prompts, upload references, review generated results, and organize assets.

### 2) Application/API Layer (Backend)
The backend receives requests from the frontend, validates them, applies business rules, and routes each request to the appropriate generation pipeline.

### 3) AI Integration Layer
Provider-specific adapters isolate external AI APIs from the rest of the codebase. This allows the platform to support multiple providers while keeping a consistent product experience.

### 4) Data & Workflow Layer
Generated outputs and metadata are stored and made available to features such as library browsing, project grouping, and storyboard-oriented workflows.

## Typical Generation Request Flow
1. A user submits a prompt (and optional references) in the studio UI.
2. The frontend sends a standardized request to the backend.
3. The backend determines the correct pipeline and validates request constraints.
4. The integration layer calls the selected AI provider.
5. Provider output is normalized into a common result format.
6. The frontend displays results and can persist them into library/project workflows.

## Why This Architecture Is Useful
- **Scalable:** New generation capabilities can be added without redesigning the entire app.
- **Maintainable:** Provider-specific complexity stays isolated in adapters.
- **Secure by Design:** Sensitive integration configuration stays on the server side.
- **Product-Consistent:** Users get a unified workflow even when underlying AI providers differ.
- **Portfolio-Ready:** Clear layering and modularity make the system understandable to technical and non-technical stakeholders.
