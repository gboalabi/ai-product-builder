# DICOS Development Workflow

## Development Process
DICOS follows a phased, docs-first delivery model:
1. Define scope and contracts in documentation/specs
2. Implement in bounded change sets
3. Verify with targeted scripts and build/type checks
4. Update implementation and development logs as part of completion criteria

This process is strongly milestone-driven, with explicit phase/subphase tracking and status governance.

## Role of AI Tools
AI-assisted engineering is used as an accelerator for:
- drafting and refining implementation plans/specs
- assisting with code generation/refactoring in bounded scopes
- producing audits/parity analyses and verification scripts
- documenting progress and cross-referencing roadmap status

Human governance remains explicit through status authority documents and acceptance criteria.

## Roadmap Structure
The repository uses phase-based planning with detailed subphase tracking. In practice, status is managed through:
- implementation plan documents (primary status authority)
- development log chronology (evidence and verification trail)
- roadmap/parity trackers for active UI and platform milestones

## Documentation System
Documentation is an operational part of delivery, not just reference material. Common document roles include:
- architecture/system design references
- phase specifications and implementation plans
- development logs with command/evidence snapshots
- parity/audit reports for UI and subsystem alignment

## Testing and Validation Approach
Validation combines automated checks and operational verification:
- TypeScript type checks and workspace builds
- targeted smoke scripts for API/worker/pipeline behaviors
- scenario-specific verification scripts for phase closeout
- system health diagnostics and run-status evidence in logs/data

The overall approach emphasizes deterministic behavior, explicit failure visibility, and evidence-backed completion.
