# Renewal Specialist Platform

## Overview
Multi-agent Copilot Studio platform supporting Renewal Specialists working with K-12 districts, universities, and community colleges.

The repository now specifies a three-section seller report: Sales Pitch Strategy, Tailored Discovery Questions, and Available Resources. Resources replace the separate internal Prep Brief. Customer deck prompts retain five slides and use the same approved education template, with customer-appropriate resource actions on Slide 5.

The 2026-09-30 changes are repository-only; runtime deployment and validation are not claimed.

## Objectives
- Meeting preparation
- Opportunity analysis
- Customer-ready drafts
- Meeting recaps
- Licensing guidance

## Architecture
See [architecture/solution-overview.md](architecture/solution-overview.md) and [architecture/agent-interactions.md](architecture/agent-interactions.md).

## Agents
See [agents](agents).

## Knowledge Sources
See /Knowledge

## Evaluations

See [Evaluations/readme.md](Evaluations/readme.md) for the Copilot Studio runtime evaluation runbook.

The evaluation package includes:

- Four importable English-language CSV test sets covering each agent and the integrated workflow
- Twenty-five runtime cases with representative expected agent responses
- Synthetic CIR and strategy fixtures that are not uploaded as runtime knowledge
- Recommended Tool use, Custom, Compare meaning, and General quality configurations
- Manual multi-turn tests for retry, refinement, state, and output pass-through

These assets are executed manually in Copilot Studio. They are not part of CI/CD or a development test pipeline. The initial runtime baseline remains pending until execution evidence is captured.

**Education/resource change status:** Evaluation files, fixtures, expected responses, imports, and execution are intentionally unchanged and paused pending user review. Existing checks expecting an internal Prep Brief do not represent the revised Section 3 contract. The future regression checklist is recorded below; static prompt/schema checks are not runtime passes.

## Releases
See [Releases/README.md](Releases/README.md).

## Significant Change Review Template
Use this template for any change that affects prompts, routing behavior, data sources, or agent boundaries.

### Summary
What is changing and why?

### Impact Analysis
Which agents, documents, and downstream outputs are affected?

### Risks
What functionality could break or regress?

### Recommended Updates
Which files should be updated to keep architecture and runtime aligned?

### Testing Recommendations
What scenarios and regressions must be validated?

### Architecture Considerations
Does this improve reuse, separation of concerns, and maintainability?

## Significant Change Review: 2026-09-30

### Summary
Expand education scope, target evidenced Copilot expansion/A3-to-A5/Azure migration/security opportunities, and replace the internal Prep Brief with Available Resources. Never assume security readiness. Keep runtime-guidance work out of scope; the user manages runtime documents separately.

### Impact Analysis
All three prompts, slide schema v1.2, architecture contracts, and release notes change together. Strategy owns resource criteria; Orchestrator passes context; Prompt Builder presents customer-appropriate actions. The report remains three sections, but replacing Section 3 is a content-contract change. No new agent, slide, tool, mandatory input, or fiscal-guidance file is introduced.

### Risks and Mitigations
- A product target could override customer evidence: retain adoption-led behavior, no-fabrication rules, and independent readiness checks.
- A threshold could be mistaken for guaranteed access: use strict comparisons, mark ambiguous counts unknown, and separate criteria from availability.
- ETC confirmation or partner details could be invented: require explicit seller confirmation for ETC; keep partner references generic and internal.
- Consumers could expect the removed Prep Brief: update handoff descriptions and version the Section 3 replacement; do not relocate the brief.
- Seller content could leak into a customer deck: restrict Slide 5 actions and exclude internal notes from presenter notes too.
- Slide 4 still requires one evidence-supported product: no slide/title redesign is authorized. Preserve neutral gap handling; never manufacture a product recommendation for a migration or adoption discussion.

### Recommended Updates
The three agent prompts, [slide schema](Knowledge/slide-schema.md), [solution overview](architecture/solution-overview.md), [handoff contracts](architecture/agent-interactions.md), and [release record](Releases/README.md) form the change set. Runtime publication is separate from repository edits.

### Testing Recommendations (Deferred)
No evaluation asset edits or execution until user approval. After review, cover K-12/university/community-college terminology; revised three-section output; every assessment threshold at equality and above; Master Class AND conditions; missing/ambiguous counts; Copilot with unknown or inadequate security readiness; seller-confirmed versus pending ETC; partner reference-only behavior; and customer/seller content separation.

Retain all six baseline scenarios: prep-only, deck-only with prior strategy, full workflow, missing CIR, worker error/retry, and follow-up refinement (including resource changes). Runtime evidence remains pending. Current verification is limited to prompt lengths, static contract checks, JSON schema parsing, and scope checks.

The expanded execution instructions also need later coverage for account switches versus same-account context reuse, dependent-worker failure handling, no-resource responses treated as valid, unknown readiness distinguished from confirmed gaps, and assessment availability confirmation without promises. These remain planned cases only; no evaluation assets or runtime results are added.

### Architecture Considerations
Reuse the existing three agents and the same presentation template. Keep assessment thresholds in Strategy rather than duplicating qualification logic in Orchestrator or Prompt Builder. Preserve source priority, CIR gating, intent priority, pass-through, and retry contracts.

## Documentation Standards
Keep documentation concise, maintainable, and system-oriented.

1. Update architecture docs when behavior changes.
2. Keep agent responsibilities explicit and non-overlapping.
3. Prefer shared patterns over repeated prompt logic.
4. Mark unknowns and assumptions clearly.
5. Record compatibility-impacting changes in release notes.

## Prompt Engineering Standards
When editing prompts:

1. Preserve current functionality unless change is requested.
2. Explain why each behavior change is needed.
3. Check for overlap with existing agents before adding scope.
4. Reuse shared source-priority and guardrail patterns.
5. Validate output contracts are unchanged unless explicitly versioned.

## Definition of Done for Architecture Changes
A significant change is complete only when all items below are satisfied.

1. Architecture documentation updated.
2. Impacted prompt definitions updated consistently.
3. Evaluation scenarios updated or added.
4. Release notes updated with compatibility impact.
5. Runtime evaluation evidence confirms prep-only, deck-only, full-workflow, gating, retry, and refinement behavior in Copilot Studio.
