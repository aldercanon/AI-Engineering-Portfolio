# Solution Overview

## Purpose
This document is the architecture source of truth for the Renewal Specialist Platform.

- Runtime source of truth: Microsoft Copilot Studio
- Architecture source of truth: this GitHub repository

The repository exists to define system behavior, agent boundaries, standards, tests, and change controls so runtime updates remain consistent and maintainable.

The 2026-09-30 education/resource changes below are implemented in repository prompts and schema. Copilot Studio deployment and runtime validation are not evidenced; evaluation updates and execution are paused by user request.

## Platform Scope (Current State)

### Education Accounts
- K-12 districts, universities, and community colleges.
- Verified institution terminology; neutral "education institution" when unknown. Never infer customer priorities or readiness from segment.
- One shared approved education template; no segment-specific template selection.

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
- Seller-facing Available Resources and customer-appropriate resource next steps
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
| Orchestrator Agent | Classify intent, enforce CIR gating, route requests, coordinate workflow and retries; pass supplied segment and seller confirmation | User request, CIR, optional context, prior worker outputs | Unchanged user-ready worker output(s), next-step prompt | No strategy/resource/deck creation or eligibility decisions; no internal processing exposed; deck without prior strategy runs full workflow |
| Renewal Strategy / Discovery / Prep Agent | Select evidence-based growth areas, generate discovery, check assessment minimums, accept seller ETC confirmation | CIR, optional context including seller confirmation, approved guidance | Exactly three sections: Sales Pitch Strategy, Tailored Discovery Questions, Available Resources | No separate prep brief, fabricated facts, inferred security readiness, pricing, discounting, negotiation, or deep implementation |
| Prompt Builder Agent | Present selected strategy and customer-appropriate resource actions using the approved education template | CIR, complete Strategy output, optional context, approved guidance and public verification | Single PowerPoint Copilot prompt for five slides | No independent assessment qualification, seller-only resource notes, JSON/schema, fabricated facts, or prohibited guidance |

## Growth and Resource Ownership
- Strategy evaluates Copilot expansion, A3 to A5, Azure migration, and security upsell as evidence-based options, never quotas. Retain adoption-led positioning for low adoption; an unsupported upsell is not required.
- Copilot ownership or expansion interest does not prove security readiness. Strategy validates security, governance, data protection, and AI readiness independently; Prompt Builder preserves relevant gaps without inventing readiness.
- Assessment minimums live in [the Strategy prompt](../agents/Renewal%20Strategy%20-%20Discovery%20Prep%20Agent%20/Prompt.md). Compare CIR-confirmed quantities using strict `>`; both Master Class conditions must pass. Missing/ambiguous quantities are "to confirm," not inferred from enrollment.
- Numerical qualification, customer relevance, and service availability are distinct. Never promise assessment access or delivery from a threshold alone.
- ETC eligibility is validated by the seller during the real call/session. All valid growth opportunities qualify once seller-confirmed; the agent does not independently qualify ETC or invent confirmation.
- Partner resources are a generic seller reminder only, with no specific offerings or qualification recommendations.
- Available Resources replaces the former internal Prep Brief as Section 3. This changes the content contract even though the section count remains three; do not relocate the removed brief.
- The five-slide deck includes only customer-appropriate resource actions within existing Slide 5 fields. Internal qualification notes and generic partner reminders stay out of slides and presenter notes.
- Runtime fiscal-guidance changes and new fiscal-guidance knowledge files are excluded. Existing source priorities remain unchanged; deployment timing is not a new input gate.

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
