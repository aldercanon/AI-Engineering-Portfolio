# Evaluations

## Purpose
Define how agent behavior is validated for correctness, consistency, and regression safety.

## Evaluation Scope
- Orchestrator routing and input gating
- Strategy/Discovery/Prep output quality and guardrail compliance
- Prompt Builder output contract and evidence alignment

## Baseline Test Set

### Golden Scenarios
1. Prep only: user requests call preparation with complete Customer Intelligence Report.
2. Deck only: user requests deck with prior strategy output available.
3. Full workflow: user requests preparation and deck in one request.

### Regression Scenarios
1. Missing required report triggers single input-gating request.
2. Worker error path offers retry without fabricated content.
3. Follow-up refinement re-invokes correct worker with appended constraints.

## Pass/Fail Criteria
Pass when all conditions hold:

1. Correct agent routing per intent.
2. Required inputs enforced before invocation.
3. Output contracts preserved (no internal schemas exposed).
4. Prohibited guidance avoided (pricing, discounting, negotiation, deep implementation).
5. No fabricated customer facts.

Fail on any single violation.

## Evidence Capture
For each run, capture:

1. Scenario name and date
2. Input summary
3. Expected behavior
4. Actual behavior
5. Pass/fail result
6. Remediation owner and target date (if fail)

## Evaluation Evidence Log

### Record 1
1. Scenario name and date: Architecture documentation consistency audit (2026-07-22)
2. Input summary: Updated architecture and governance documents plus current agent prompt definitions
3. Expected behavior: Architecture docs accurately describe implemented three-agent behavior and guardrails
4. Actual behavior: Mostly aligned; minor documentation hardening items identified (naming alias and shared source-priority standardization)
5. Pass/fail result: Pass with follow-up actions
6. Remediation owner and target date (if fail): Not applicable

### Record 2
1. Scenario name and date: Release governance initialization (2026-07-22)
2. Input summary: Release template and first release entry
3. Expected behavior: Release notes include compatibility and validation traceability
4. Actual behavior: First release entry includes compatibility notes, risks, and evaluation references
5. Pass/fail result: Pass
6. Remediation owner and target date (if fail): Not applicable

### Record 3
1. Scenario name and date: Runtime scenario walkthrough status check (2026-07-22)
2. Input summary: Golden runtime scenarios defined but not executed in Copilot Studio runtime
3. Expected behavior: Scenario execution evidence available
4. Actual behavior: Pending runtime execution evidence
5. Pass/fail result: Open
6. Remediation owner and target date (if fail): Architecture owner, target 2026-07-29

