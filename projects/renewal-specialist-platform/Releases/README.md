# Releases

## Purpose
Track architecture and prompt changes with clear compatibility and risk visibility.

## Release Entry Template
Use this template for each release note entry.

### Version
Semver or dated tag.

### Date
Release date.

### Summary
What changed across architecture, prompts, or knowledge sources.

### Impacted Components
List impacted agents and documentation files.

### Compatibility Notes
State whether routing, input requirements, or output contracts changed.

### Risks and Mitigations
List expected risks and mitigation/rollback actions.

### Validation Evidence
Reference evaluation scenarios and outcomes.

## Rollback Guidance
If a release introduces regression:

1. Revert to last known good prompt versions in Copilot Studio.
2. Record incident and root cause.
3. Update evaluation coverage before re-release.

## Release Log

### Version
2026.07.22-architecture-baseline

### Date
2026-07-22

### Summary
Established architecture governance baseline across solution overview, interaction contracts, project standards, evaluations, knowledge governance, and release controls.

### Impacted Components
- Orchestrator Agent documentation
- Renewal Strategy / Discovery / Prep Agent documentation
- Prompt Builder Agent documentation
- architecture/solution-overview.md
- architecture/agent-interactions.md
- README.md
- Evaluations/readme.md
- Knowledge/readme.md
- Releases/README.md

### Compatibility Notes
- No runtime prompt contract changes were implemented in this release.
- Documentation now codifies existing routing and output-contract expectations.

### Risks and Mitigations
- Risk: Documentation-runtime drift in future changes.
- Mitigation: Require Significant Change Review Template plus release compatibility notes for each prompt update.

### Validation Evidence
- Architecture consistency audit completed: architecture/consistency-audit-2026-07-22.md
- Baseline evaluation records initialized in Evaluations/readme.md

