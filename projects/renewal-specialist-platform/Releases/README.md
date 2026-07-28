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
2026.07.28-website-grounding-agents

### Date
2026-07-28

### Summary
Added organization website URL as optional grounding source across Orchestrator, Renewal Strategy/Discovery/Prep Agent, and Prompt Builder Agent. Website enables agents to extract organization mission statement and strategic priorities to inform consultative messaging, particularly the "Microsoft + Org message" section in renewal decks. Website positioned as Tier 6 (lowest priority) in source hierarchy—does not override Customer Intelligence Report facts. Orchestrator now accepts and passes website URL to worker agents.

### Impacted Components
- Orchestrator Agent: Added organization website as optional parameter; updated routing to pass website URL to both worker agents
- Renewal Strategy / Discovery / Prep Agent: Added website as Tier 6 source in SOURCE PRIORITY hierarchy; included cross-reference safeguards
- Prompt Builder Agent: Updated DATA SOURCES section to include organization website; enhanced "Microsoft + Org message" schema field with website-informed context; updated Slide 2 content rules
- Releases/README.md: New release entry

### Compatibility Notes
- **Input Contract Change:** Orchestrator now accepts optional `organization_website` parameter alongside Customer Intelligence Report. If not provided, existing behavior unchanged.
- **Output Contract:** No change. All three agents continue returning user-ready outputs only; website grounding affects narrative/context only, not licensing or compliance facts.
- **Routing:** No change to routing logic. Orchestrator still routes to exactly two worker agents; website URL flows through orchestrator context (like CIR).
- **Backward Compatibility:** Existing workflows without website URL continue unchanged. Website grounding is purely additive and optional.

### Risks and Mitigations
- **Risk:** Organization website unavailable or mission statement not found.
  - **Mitigation:** Agents explicitly note fallback behavior; no fabrication of organizational narrative. Slide 2 presenter notes document source ("website provided" vs "CIR-sourced").
- **Risk:** Website information conflicts with CIR licensing/usage facts.
  - **Mitigation:** Explicit source priority rule: CIR is authoritative; website informs narrative only. Renewal Strategy Agent flags discrepancies; Prompt Builder maintains CIR as ground truth.
- **Risk:** Website URL format errors or malformed URLs.
  - **Mitigation:** Orchestrator passes URL as-is; agents handle gracefully without blocking workflow.

### Validation Evidence
- Manual verification: Orchestrator correctly passes website URL to both worker agents in all three intent flows (INTENT A, B, C)
- Manual verification: Renewal Strategy Agent respects source priority; CIR facts not overridden by website context
- Manual verification: Prompt Builder "Microsoft + Org message" section synthesizes website mission + CIR agreement facts without contradiction
- Fallback testing: Verified agents note explicitly when website unavailable (no fabrication)
- Backward compatibility: Verified existing workflows without website URL produce identical results to baseline (2026.07.22)

### Rollback Guidance
If website grounding introduces unexpected behavior:
1. Revert Orchestrator, Renewal Strategy Agent, and Prompt Builder prompts to 2026.07.22 baseline versions.
2. Restore website parameter handling to not-applicable state in Orchestrator Step 2.
3. Disable website URL input from Orchestrator routing (INTENT A, B, C).
4. Remove website from SOURCE PRIORITY hierarchy in Renewal Strategy Agent.
5. Restore Prompt Builder Slide 2 schema to pre-2026.07.28 state (no website field).
6. Record incident, review cross-reference safeguards, and re-test before next release.

---

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

