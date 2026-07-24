---
applyTo: "projects/renewal-specialist-platform/agents/**/Prompt.md"
description: "Always-on operational prompt-engineering workflow for any requested prompt change. Trigger when user asks to apply a change in prompt files."
---

# Prompt Change Workflow (Always On)

When a prompt file in this project is edited, apply this workflow automatically.
Do not require the user to explicitly invoke a skill or workflow.

## Required Intake Before Editing
Collect only missing items:
1. Operational change summary.
2. Affected agent(s).
3. Effective date and urgency.
4. Compatibility requirement (strict or flexible).
5. Validation scope.

## Editing Rules
1. Preserve existing behavior unless explicit change is requested.
2. Prefer minimal prompt deltas over full rewrites.
3. Maintain strict role boundaries across the three-agent model.
4. Keep source-priority and no-fabrication rules intact.
5. Do not introduce pricing, discounting, negotiation, or deep implementation guidance.

## Required Output Shape
Return updates in this order:
1. Change impact summary.
2. Prompt delta proposals by agent.
3. Validation and regression plan.
4. Documentation update list.
5. Release note draft.
