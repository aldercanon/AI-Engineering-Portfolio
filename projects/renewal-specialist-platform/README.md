# Renewal Specialist Platform

## Overview
Multi-agent Copilot Studio platform supporting Renewal Specialists.

## Objectives
- Meeting preparation
- Opportunity analysis
- Customer-ready drafts
- Meeting recaps
- Licensing guidance

## Architecture
See /architecture

## Agents
See /agents

## Knowledge Sources
See /Knowledge

## Evaluations
See /Evaluations

## Releases
See /Releases

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
5. Baseline scenario walkthroughs pass (prep only, deck only, full workflow).
