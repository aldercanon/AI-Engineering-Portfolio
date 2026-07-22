# Architecture-Prompt Consistency Audit (2026-07-22)

## Summary
This audit compares architecture documentation to implemented prompt behavior for the three-agent system.

Overall status: Mostly aligned, with a small number of documentation-level inconsistencies to address.

## Findings (Ordered by Severity)

### High
None.

### Medium
1. Deck-only flow dependency is implicit in architecture, but prompt behavior has a stricter fallback.
- Prompt behavior: If a user asks for a deck and no prior strategy output exists, orchestrator reclassifies to full workflow.
- Architecture status: Documented in interaction lifecycle, but not clearly restated in responsibilities matrix notes.
- Risk: Future edits may accidentally bypass strategy-first dependency for deck quality.
- Recommendation: Keep this dependency explicitly visible in both interaction and responsibilities sections.

2. Source-priority model is not yet uniformly expressed as a reusable canonical block across all prompts.
- Prompt behavior: Strategy and Prompt Builder define detailed source-ordering; Orchestrator focuses on routing and required input gating.
- Architecture status: Shared pattern defined, but practical reuse implementation notes are still abstract.
- Risk: Drift in source precedence language between worker prompts over time.
- Recommendation: Introduce a single canonical "Source Priority Block" text snippet in architecture docs and reference it during prompt updates.

### Low
1. Naming variance remains possible across docs and runtime labels.
- Prompt names include "Elevate Draft Prompt Builder" while architecture uses "Prompt Builder Agent".
- Risk: Traceability friction in reviews and release notes.
- Recommendation: Maintain alias mapping in one location.

## Impact Analysis
Affected agents:
- Orchestrator Agent
- Renewal Strategy / Discovery / Prep Agent
- Prompt Builder Agent

Affected documentation:
- architecture/solution-overview.md
- architecture/agent-interactions.md
- README.md

## Risks
1. Contract drift if runtime prompt edits are not mirrored in repository docs.
2. Routing regressions if deck-only preconditions are relaxed unintentionally.
3. Knowledge governance drift if source-ordering language diverges across prompts.

## Recommended Updates
1. Add an alias map and canonical naming rule in architecture docs.
2. Add a reusable source-priority snippet template in architecture docs.
3. Ensure release entries always include naming and contract compatibility notes.

## Testing Recommendations
1. Validate deck-only requests with and without prior strategy output.
2. Validate full workflow produces strategy-first then deck generation.
3. Validate no worker exposes internal schemas or hidden reasoning artifacts.
4. Validate source conflict handling keeps Customer Intelligence Report authoritative.

## Architecture Considerations
The current architecture improves maintainability and separation of concerns. Remaining gaps are documentation hardening opportunities, not structural blockers.
