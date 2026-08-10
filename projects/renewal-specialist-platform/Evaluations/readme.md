# Copilot Studio Runtime Evaluations

## Purpose

Validate the three-agent workflow directly in Copilot Studio. These evaluations are runtime assets only. They are not part of a development pipeline, CI/CD gate, or automated test framework.

The repository versions the importable CSV files, synthetic fixtures, evaluator guidance, manual conversation tests, and runtime evidence.

## Test Set Inventory

| File | Import target | Cases |
|---|---|---:|
| `test-sets/orchestrator.csv` | Orchestrator Agent | 8 |
| `test-sets/strategy-agent.csv` | Renewal Strategy / Discovery / Prep Agent | 6 |
| `test-sets/prompt-builder.csv` | Elevate Draft Prompt Builder | 6 |
| `test-sets/workflow-e2e.csv` | Published Orchestrator with connected agents | 5 |

All test questions and expected responses are in English. Expected responses are representative correct agent answers, not instructions describing what the agent should do.

## Import Constraints

The files follow `EvaluationTemplate.csv`:

- Columns: `question`, `expectedResponse`
- Maximum 100 questions per import
- Maximum 500 characters per question, including spaces
- Test methods are configured in Copilot Studio after import
- Evaluation metadata is excluded from questions to avoid influencing agent behavior

Before import, confirm that the CSV opens as UTF-8, has exactly two columns, contains no empty values, and stays within the row and question limits.

## Test Methods

Use methods that evaluate different dimensions instead of stacking text-comparison methods that conflict.

### Orchestrator

Use **Tool use + Custom** as the primary combination. Tool use validates routing and invocation order; Custom validates gating, boundaries, and guardrails. Add **Compare meaning** for visible gating, clarification, and refusal behavior. Use **General quality** when reviewing long worker outputs returned through the Orchestrator.

### Strategy Agent

Use **Custom + Compare meaning**. Custom validates strategy selection, source precedence, the three-section contract, unknown handling, and guardrails. Compare meaning checks the response against a representative correct answer. Add **General quality** for completeness and relevance.

### Prompt Builder

Use **Custom + Compare meaning**. Custom validates the sole-visible-output rule, five-slide structure, required content, no-fabrication behavior, and guardrails. Add **General quality** for the complete prompt. Add **Tool use** only when web and knowledge calls are exposed to the evaluator.

### End-to-End

Use **Tool use + Custom**, with **General quality** for the final user experience. Use Compare meaning for deterministic gating and refusal cases.

Do not use Text similarity for these generative responses. Do not use Exact match across an entire suite. Keyword match is unnecessary for the baseline because Custom can evaluate required concepts without encouraging keyword stuffing.

The exact Custom instructions and row-level method recommendations are in `case-catalog.md`.

## Runtime Execution

1. Import each CSV into its stated target.
2. Configure the recommended methods from `case-catalog.md`.
3. Start with a 70% threshold for Compare meaning.
4. Run contract-critical cases first.
5. Run each generative baseline case three times.
6. Execute `manual-workflow-tests.md` for conversation state, retry, refinement, and pass-through behavior.
7. Capture runtime evidence before changing prompts or expected responses.

## Result Interpretation

A result passes only when all configured methods support the contract being tested. A fluent answer does not compensate for incorrect routing, fabricated facts, exposed schemas, missing sections, or prohibited guidance.

- **P0:** Contract-critical. Review immediately and do not accept the runtime baseline while failing.
- **P1:** Semantic quality or consistency. Review repeated failures and material omissions.
- **P2:** Trend observation. Nonblocking; none are included in the initial baseline.

If a result fails, compare the direct-worker set with the end-to-end set:

- Direct worker fails: investigate that worker's prompt, grounding, or tools.
- Direct worker passes and end-to-end fails: investigate routing, handoff context, or output pass-through.
- Tool use passes and content fails: investigate the worker output contract or grounding.
- Content passes and Tool use fails: investigate routing or tool selection.

## Resilience Policy

Keep stable contracts strict and mutable business language flexible.

- Preserve source priority, required input gating, role boundaries, output shape, no-fabrication rules, and prohibited-guidance rules as hard expectations.
- Evaluate meaning rather than exact prose.
- Avoid locking tests to a specific product recommendation unless the fixture explicitly proves that recommendation.
- Mark missing facts as `under review` or `to confirm` instead of inventing values.
- Update expected responses only when an approved business or architecture change alters correct behavior.
- Document the reason for every baseline change; never weaken an expected response solely to clear a failure.

## Synthetic Data

The fixtures under `fixtures/` are fictional and cover:

- Low and uneven adoption
- Strong adoption with documented capability gaps
- Incomplete and conflicting evidence
- Controlled Strategy A and Strategy B handoffs

Fixtures are evaluation references only. Do not upload them as runtime knowledge, because retrieval could contaminate unrelated evaluation cases.

### Data Privacy Rule

Never place real customer data in evaluation fixtures, CSV questions, expected responses, manual tests, evidence examples, or screenshots committed to this repository.

- Use only `Synthetic K-12 District Alpha`, `Synthetic K-12 District Beta`, and `Synthetic K-12 District Gamma` as organization identities.
- Use `Fictional City` and `Fictional State` for locations.
- Use reserved `.example` domains and `SYN-` prefixes for identifiers.
- Do not copy tenant IDs, subscription GUIDs, domains, email addresses, URLs, agreement numbers, customer names, or exact customer metrics from production sources.
- Treat all quantities, dates, adoption metrics, insights, and signals in this package as invented evaluation data.
- Before import or commit, scan the full `Evaluations/` directory for customer names and identifiers from the source material used to design a scenario.

## Evidence Log

For each runtime run, capture:

1. Case reference and date
2. Published agent version and environment
3. Configured test methods and thresholds
4. Input summary
5. Tool or topic invocations and order
6. Actual response
7. Method-level scores or labels
8. Overall pass or fail
9. Remediation owner and target date when failing

### Open Baseline Record

- Scenario: Initial runtime evaluation baseline
- Status: Pending import and execution in Copilot Studio
- Expected evidence: Direct-agent sets, end-to-end set, and manual stateful workflow results
- Completion rule: Runtime results are recorded for all P0 cases; no documentation-only walkthrough counts as a runtime pass

