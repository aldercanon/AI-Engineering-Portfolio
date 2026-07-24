---
name: operational-prompt-engineering
description: Use when the user asks to generate, revise, refactor, or validate Copilot Studio agent prompts due to operational changes, policy updates, process changes, routing changes, or governance updates.
---

# Operational Prompt Engineering

## Purpose
Translate operational changes into safe, testable prompt updates across the Renewal Specialist Platform.

## Use When
- Operational process changed and prompts must be updated.
- Guardrails or compliance language changed.
- Routing or handoff rules changed between agents.
- Output contract needs refinement without breaking compatibility.
- User asks for prompt regeneration based on new business reality.

## Required Inputs
Collect these first:
1. Operational change summary (what changed and why).
2. Affected agent(s): Orchestrator, Strategy/Discovery/Prep, Prompt Builder.
3. Effective date and urgency.
4. Backward compatibility requirement: strict or flexible.
5. Validation scope required by the user.

If any required input is missing, ask only for missing items.

## Working Rules
1. Preserve existing behavior unless explicit change is requested.
2. Prefer minimum viable prompt deltas over full rewrites.
3. Keep role boundaries strict across the three-agent model.
4. Do not introduce prohibited guidance: pricing, discounting, negotiation, deep implementation.
5. Keep source-priority and no-fabrication guarantees intact.
6. If scope is ambiguous, stop and request clarification before editing prompts.

## Execution Workflow
1. Map impact:
- Identify impacted files and contracts.
- State expected behavior before and after the change.

2. Propose prompt deltas:
- Provide explicit old behavior vs new behavior.
- Use patch-style sections for each prompt block.
- Keep wording deterministic and testable.

3. Validate architecture consistency:
- Check alignment with architecture and interaction docs.
- Call out required documentation updates.

4. Produce regression checklist:
- Prep-only
- Deck-only with prior strategy output
- Full workflow
- Missing input gating
- Worker error retry path
- Follow-up refinement routing

5. Produce release-ready summary:
- Compatibility notes
- Risks and mitigations
- Evidence expectations

## Output Contract
Return results in this exact order:
1. Change Impact Summary
2. Prompt Delta Proposals (by agent)
3. Validation and Regression Plan
4. Documentation Update List
5. Release Notes Draft

## Project File Priorities
Prioritize these files when performing updates:
- projects/renewal-specialist-platform/agents/Orchestrator-Agent/Prompt.md
- projects/renewal-specialist-platform/agents/Renewal Strategy - Discovery Prep Agent /Prompt.md
- projects/renewal-specialist-platform/agents/Prompt-Builder/Prompt.md
- projects/renewal-specialist-platform/architecture/solution-overview.md
- projects/renewal-specialist-platform/architecture/agent-interactions.md
- projects/renewal-specialist-platform/Evaluations/readme.md
- projects/renewal-specialist-platform/Releases/README.md

## Failure Policy
If a requested change would break agent boundaries, hide internal schemas, or violate guardrails, refuse that part and provide a compliant alternative.
