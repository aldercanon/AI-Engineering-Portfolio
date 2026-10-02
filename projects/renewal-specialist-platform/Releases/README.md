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
2026.09.30-education-resources (repository implementation; runtime validation pending)

### Date
2026-09-30 (repository change date, not a deployment date)

### Summary
Expanded scope to K-12 districts, universities, and community colleges. Added evidence-based Copilot expansion, A3-to-A5, Azure migration, and security growth targeting without assuming security readiness. Replaced the seller's Section 3 internal Prep Brief with Available Resources. Retained five customer slides using the same approved education template and customer-appropriate resource actions on Slide 5.

Follow-up refinement uses additional prompt space at the user's request: explicit evidence-to-recommendation steps, account-specific context reuse, dependent-worker failure handling, assessment interpretation, and seller-to-customer content filtering. No additional output sections, slides, resource thresholds, or runtime-guidance capabilities are introduced.

### Impacted Components
- All three agent prompts: education scope, resource ownership, revised report handoff, and shared template wording.
- Knowledge/slide-schema.md: v1.2 education metadata and Slide 5 resource constraints; required field shapes unchanged.
- architecture/solution-overview.md and architecture/agent-interactions.md: ownership, compatibility, and seller/customer content separation.
- Project README.md: significant-change review and deferred regression plan.
- Evaluation assets and runtime configuration: no changes or execution in this implementation.

### Compatibility Notes
- Strategy still returns three sections, but Section 3 is now Available Resources. Consumers expecting an internal Prep Brief must update; this is a content-contract change.
- Deck count/order and Slide 4's one-product structure remain unchanged. Historical Strategy outputs do not establish resource eligibility; refresh preparation when new resource recommendations are needed.
- Orchestrator retains intent priority, required CIR, full-workflow fallback, unchanged worker output pass-through, and retry behavior. Resource-only requests and resource/confirmation refinements explicitly route to Strategy.
- Assessment minimums use strict `>` and CIR-confirmed quantities, with both Master Class conditions required. Criteria met does not guarantee relevance, readiness, or availability.
- ETC eligibility remains seller-validated during the call/session; accept explicit confirmation, never infer it. Partner resources remain generic seller references, not specific offers or recommendations.
- No fiscal-guidance file, new fiscal-year logic, timing gate, new template, agent, connector, or evaluation package is added.

### Risks and Mitigations
- **Unsupported upsell or implied security readiness:** Strategy requires evidence and validates readiness independently; deck content preserves relevant gaps.
- **False resource qualification:** Strict thresholds, unknown handling for ambiguous quantities, and separate availability checks; no delivery promises.
- **Seller details exposed:** Exclude internal criteria/status notes and partner reminders from slides and presenter notes; require seller-confirmed ETC before customer actions.
- **Contract drift:** Version the Section 3 replacement and schema together. Deploy the matching prompts/schema as a coordinated set; old evaluation expectations require later user-approved revision.
- **Runtime regression:** Static checks are not runtime evidence. Evaluation updates and execution are paused by user request; runtime readiness is not asserted.
- **Reduced prompt headroom:** More operational detail intentionally exceeds the preferred 5,600-6,000-character target. Retain the hard 8,000-character limit and recheck counts after every edit; smallest remaining margin is 229 characters.

### Validation Evidence
- Static prompt character counts: Orchestrator 7,529; Strategy 7,667; Prompt Builder 7,771. All below the hard 8,000-character limit, leaving 471, 333, and 229 characters respectively.
- Static checks passed for three Strategy sections, supplied assessment-rule text, CIR/context handoffs, intent order, and readiness/ETC safeguards.
- Slide schema JSON parsed with exactly five ordered slides and unchanged Slide 5 field names.
- Runtime deployment, evaluation imports, and execution: not performed. Baseline scenarios remain unvalidated for this change.
- Deferred coverage: education segments, section replacement, thresholds and unknowns, readiness gaps, ETC confirmation, partner references, seller/customer separation, plus prep-only, deck-only, full workflow, missing CIR, worker retry, and refinement.
- Additional deferred edge cases: same-account reuse versus account switch, Strategy failure halting full workflow, deck-only worker retry, unknown/no-resource outputs accepted as complete, unknown readiness without asserting insecurity, and resource availability confirmation without delivery promises.

### Rollback Guidance
If published behavior regresses, restore the last known-good versions of all three prompts and the matching slide-schema knowledge document together in Copilot Studio. Restore the old three-section meaning (including Prep Brief), K-12-only scope/template wording, and previous resource behavior. Update repository contracts to match the restored runtime; preserve existing evaluation assets while review remains paused and record the incident. This entry does not authorize publication or claim a runtime pass.

---

### Version
2026.08.10-runtime-evaluation-baseline

### Date
2026-08-10

### Summary
Added a versioned Copilot Studio runtime evaluation package for the Orchestrator, Renewal Strategy / Discovery / Prep Agent, Prompt Builder, and integrated workflow. The package includes 25 English-language import cases, representative expected agent responses, synthetic fixtures, evaluator configuration guidance, and manual multi-turn tests.

### Impacted Components
- Evaluations/readme.md: Runtime-only import, execution, triage, and evidence runbook
- Evaluations/case-catalog.md: Row-level coverage, priority, method selection, and Custom evaluator instructions
- Evaluations/test-sets/: Four importable CSV files
- Evaluations/fixtures/: Three synthetic CIR profiles and controlled strategy handoffs
- Evaluations/manual-workflow-tests.md: Stateful retry, refinement, and pass-through scenarios
- README.md, projects/readme.md, and repository README.md: Navigation and evaluation scope
- Knowledge/readme.md: Explicit separation between synthetic fixtures and runtime knowledge

### Compatibility Notes
- **Runtime behavior:** No change to prompts, routing, tools, inputs, or output contracts.
- **Evaluation operation:** Test sets are imported and executed manually in Copilot Studio; no CI/CD or development pipeline integration was added.
- **Language:** All imported questions and expected responses are in English.
- **Expected responses:** Each value is a representative correct agent answer for semantic comparison, not an instruction describing expected behavior.

### Risks and Mitigations
- **Risk:** Generative wording differs from the representative expected response.
  - **Mitigation:** Use Compare meaning rather than Text similarity or suite-wide Exact match; use Custom for structural contracts.
- **Risk:** Evaluation metadata influences agent routing or output.
  - **Mitigation:** Keep IDs and priorities in the external case catalog, not in CSV questions.
- **Risk:** Synthetic fixture facts are retrieved during unrelated runtime cases.
  - **Mitigation:** Keep fixtures repository-only and do not upload them as Copilot Studio knowledge.
- **Risk:** Documentation is mistaken for runtime validation evidence.
  - **Mitigation:** Initial baseline status remains pending until all P0 runtime results are recorded.

### Validation Evidence
- CSV structure validated for exact `question` and `expectedResponse` columns
- 25 total cases across four files; all questions are below the 500-character import limit
- English-language scan completed for all imported questions
- Privacy scan completed: no source customer names, domains, tenant IDs, subscription GUIDs, agreement identifiers, email addresses, or URLs are present; all scenario data is explicitly fictional
- Runtime import and execution evidence: Pending in Copilot Studio

### Rollback Guidance
Remove the imported test sets from Copilot Studio if they interfere with evaluation operations. Repository evaluation assets can be reverted independently because no runtime prompts or architecture contracts changed.

---

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

