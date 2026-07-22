# Solution Overview

## Purpose
This document is the architecture source of truth for the Renewal Specialist Platform.

- Runtime source of truth: Microsoft Copilot Studio
- Architecture source of truth: this GitHub repository

The repository exists to define system behavior, agent boundaries, standards, tests, and change controls so runtime updates remain consistent and maintainable.

## Platform Scope (Current State)

### In Scope
- Microsoft Copilot Studio agents
- Power Platform solution packaging
- SharePoint-hosted knowledge sources
- Uploaded files used for grounding

### Not Yet Implemented
- Power Automate flows
- Custom connectors
- External APIs
- CRM integration

## Users
- Renewal Specialists
- Sales Managers

## Key Functions
- Session preparation
- Opportunity analysis
- Discovery support
- Customer-facing deck prompt generation

## Architecture Principles
1. Simplicity over complexity.
2. Reuse over duplication.
3. Shared patterns whenever possible.
4. Agent responsibilities must remain clearly separated.
5. Evaluate existing agents before creating new ones.
6. Minimize maintenance burden with every change.
7. Keep behavior consistent across agents.

## Current Agent Model
The current implemented model is intentionally simple and contains three agents.

1. Orchestrator Agent (entry point)
2. Renewal Strategy / Discovery / Prep Agent (combined worker agent)
3. Prompt Builder Agent

Note: Strategy and discovery remain combined by design in the current phase.

## Naming and Alias Map
Use these canonical names in architecture and release notes.

- Orchestrator Agent
- Renewal Strategy / Discovery / Prep Agent
- Prompt Builder Agent

Known runtime/prompt aliases:

- Prompt Builder Agent = Elevate Draft Prompt Builder

## Responsibilities Matrix
| Agent | Primary Responsibilities | Inputs | Outputs | Non-Goals / Guardrails |
| --- | --- | --- | --- | --- |
| Orchestrator Agent | Classify intent, enforce required input gating, route requests, coordinate multi-step workflow, handle retries | User request, Customer Intelligence Report, prior worker outputs | Final user-ready worker output(s), next-step prompt to continue workflow | Must not generate strategy/discovery/deck content itself; must not expose internal processing; must not fabricate data; deck-only request without prior strategy must run full workflow first |
| Renewal Strategy / Discovery / Prep Agent | Produce consultative strategy, discovery questions, and internal prep brief from evidence | Customer Intelligence Report, optional context, approved internal guidance | Structured strategy/discovery/prep response | No pricing, discounting, negotiation, or deep implementation guidance; no invented customer facts |
| Prompt Builder Agent | Produce ready-to-paste PowerPoint Copilot prompt aligned to selected strategy and evidence | Customer Intelligence Report, strategy output, approved guidance and public verification context | Single clean PowerPoint Copilot prompt | No JSON/internal schema in output; no fabricated data; no pricing/discounting/deep technical guidance |

## Shared System Behavior
All agents must follow shared rules unless a stricter agent-specific rule exists.

- Source-of-truth precedence: user-provided customer intelligence over lower-priority sources.
- Unknown handling: clearly mark unknown or missing values; never estimate sensitive values.
- Safety and scope: avoid manipulative language and prohibited advisory areas.
- Output contracts: each agent returns only the expected output type for its role.

## Change Evaluation Rule
Every new capability request must answer these questions before implementation:

1. Can an existing agent own this behavior without violating separation of concerns?
2. Is there duplicated logic that should become a shared pattern instead?
3. Does the change alter input/output contracts between agents?
4. Does the change increase long-term maintenance cost?

If any answer is unclear, architecture review is required before prompt updates.

## Future Capabilities Guardrails

### CRM Integration
- Introduce CRM only through well-defined boundaries and explicit ownership.
- Keep orchestration and business logic in agents; keep integration adapters isolated.
- Preserve current prompt contracts unless a versioned change is approved.

### Additional Specialized Agents
Create a new agent only when all conditions are true:

1. The behavior cannot be safely absorbed by an existing agent.
2. The behavior has distinct inputs, outputs, and ownership.
3. Reuse and consistency patterns are documented first.
4. Evaluation cases and release notes are prepared before runtime deployment.

## Related Documents
- `architecture/agent-interactions.md` for request lifecycle and handoff contracts.
- `README.md` for governance process and significant change review template.
