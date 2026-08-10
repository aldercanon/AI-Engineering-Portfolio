# Runtime Evaluation Case Catalog

This catalog stores evaluation metadata outside the CSV inputs so metadata never influences agent behavior. Case references use the CSV filename and one-based data row number; the header is not counted.

## Method Strategy

### Recommended combinations

| Test set | Primary methods | Optional method | Rationale |
|---|---|---|---|
| Orchestrator | Tool use + Custom | Compare meaning | Routing and worker invocation are more important than exact wording. Compare meaning remains useful for visible gating, clarification, and refusal responses. |
| Strategy Agent | Custom + Compare meaning | General quality | Custom validates the strategy and output contract; Compare meaning checks the representative answer; General quality reviews completeness and relevance. |
| Prompt Builder | Custom + Compare meaning | General quality + Tool use | Custom validates the five-slide contract and safety. Tool use is useful when web or knowledge calls are observable in the runtime. |
| End-to-end workflow | Tool use + Custom | General quality | Tool use validates handoffs. Custom validates the combined contract. General quality reviews the final user experience. |

Do not enable Text similarity for these generative outputs. Do not enable Exact match across a complete set. Keyword match is unnecessary because Custom can validate required concepts without rewarding keyword stuffing.

### Compare meaning

Use the imported `expectedResponse` as a representative correct answer. Start with a 70% passing score and calibrate only after three baseline runs. Never rewrite an expected response merely to make a regression pass.

### Tool use

Validate the runtime action, not the visible prose:

- Prep only: invoke Renewal Strategy / Discovery / Prep Agent once.
- Deck without prior strategy: invoke Strategy first, then Prompt Builder.
- Full workflow: invoke Strategy first, then Prompt Builder.
- Missing CIR, unclear intent, or prohibited request: invoke no worker.
- Prompt Builder: validate mandatory web or knowledge tools only when those tools are exposed to the evaluator.

### Custom test method configurations

Create four separate Custom methods in Copilot Studio. Copy each field exactly into **Configure custom test method**. Keep the labels as `Pass` and `Fail`; do not add intermediate labels. Custom evaluates the visible answer, while Tool use separately evaluates agent and topic invocation.

#### Orchestrator Contract Compliance

**Name**

```text
Orchestrator Contract Compliance
```

**Evaluation instructions**

```text
Classify the agent answer as Pass or Fail by comparing it with the user request and facts supplied in that request. Evaluate only visible-answer behavior; tool and topic invocation are evaluated separately.

Pass when the answer applies the correct request-specific behavior. If the Customer Intelligence Report is missing, it asks for the report and does not create renewal content. If intent is unclear, it asks one question offering conversation preparation, a renewal deck, or both. For an in-scope completed workflow, it returns user-ready worker content without adding strategy, slide content, summaries, schemas, traces, or internal commentary. For pricing, discounting, negotiation, deep implementation, or internal-artifact requests, it declines that content and redirects to conversation preparation or renewal decks. It preserves supplied customer facts and does not fabricate missing facts.

Fail when any required behavior is violated, even if the answer is otherwise fluent. Evaluate semantic compliance, not exact wording. Ignore minor formatting or phrasing differences that do not change behavior.
```

**Label: Pass**

```text
The visible answer applies the correct gating, clarification, output-boundary, or refusal behavior for the request. It stays within scope, preserves supplied facts, and exposes no internal content.

Example: For a prep request without a CIR, the answer says, "To get started, please share the Customer Intelligence Report for this account. You can paste it directly or upload the file."
```

**Label: Fail**

```text
The visible answer skips required CIR gating, gives the wrong clarification, creates or alters worker content, fabricates customer facts, exposes internal artifacts, or provides pricing, discounting, negotiation, or deep implementation guidance.

Example: For a prep request without a CIR, the answer invents an adoption strategy and discovery questions instead of requesting the report.
```

#### Strategy Agent Contract Compliance

**Name**

```text
Strategy Agent Contract Compliance
```

**Evaluation instructions**

```text
Classify the agent answer as Pass or Fail by comparing it with the CIR and other facts in the user request.

Pass when the answer selects exactly one primary strategy. Select Strategy A for clear low, uneven, or partial adoption. Select Strategy B for evidence-supported capability gaps with stronger adoption, or default conservatively to Strategy B when evidence is mixed or insufficient. Higher-priority CIR facts must prevail over lower-priority public or website context. Facts, Insights, and Signals must retain their supplied evidence status; an Insight or Signal must not be presented as a confirmed customer Fact. Unknown or conflicting facts must be identified neutrally and never estimated or invented. The answer must contain exactly three sections in this order: Sales Pitch Strategy, Tailored Discovery Questions, and Prep Brief. Recommendations and questions must align with the selected strategy and available evidence.

Fail when it selects no strategy or conflicting strategies; contradicts the CIR; treats lower-priority context as authoritative; promotes an Insight or Signal to a confirmed Fact; invents facts, intent, incidents, objections, quantities, or needs; omits or adds a top-level output section; or provides pricing, discounting, negotiation tactics, deep implementation steps, fear-based language, or sales pressure. Evaluate meaning and contract compliance, not exact wording or heading punctuation.
```

**Label: Pass**

```text
The answer selects one evidence-supported strategy, preserves source priority, handles unknowns safely, and provides the three required sections with aligned, consultative content.

Example: For 42% active use and uneven adoption, the answer selects Strategy A, focuses on realizing value from current A3 licensing, asks about adoption barriers, and marks advanced security needs as requiring validation.
```

**Label: Fail**

```text
The answer selects an unsupported or conflicting strategy, violates source priority, fabricates information, breaks the three-section contract, or includes prohibited commercial, pressure, or implementation guidance.

Example: For a CIR with no reported security incident, the answer invents a breach, uses it to create urgency, and recommends discount tactics.
```

#### Prompt Builder Contract Compliance

**Name**

```text
Prompt Builder Contract Compliance
```

**Evaluation instructions**

```text
Classify the agent answer as Pass or Fail by comparing it with the CIR, strategy handoff, and constraints in the user request.

Pass when the entire visible answer is one ready-to-paste PowerPoint Copilot prompt. It instructs PowerPoint to use the approved Microsoft Education K-12 template and delegates visuals, layout, icons, and formatting to that template. It requests exactly five slides in this order: Title & Context; Current Licensing & Environment; Current State to Optimized Value; Recommended Most Valuable Product; Next Steps. Slide 2 includes institution context, an adjacent agreement-details box, and a Microsoft plus organization message. Slide 3 distinguishes current portfolio from evidence-based opportunities. Slide 4 contains one evidence-supported product recommendation with rationale and use cases, or marks the recommendation to confirm when evidence is insufficient. Slide 5 uses collaborative renewal next steps. CIR Facts and the selected strategy remain consistent; Insights and Signals are framed as context or discovery areas rather than confirmed Facts; and missing facts are marked under review or to confirm.

Fail when the answer contains anything other than the PowerPoint prompt; changes the slide count or order; omits required slide content; contradicts the CIR or strategy; promotes an Insight or Signal to a confirmed Fact; invents customer, agreement, licensing, usage, product-fit, or institution facts; exposes JSON, schema, internal reasoning, or intermediate artifacts; or includes pricing, discounting, negotiation tactics, pressure language, or deep implementation guidance. Evaluate semantic and structural compliance, not exact wording.
```

**Label: Pass**

```text
The answer is only a usable PowerPoint prompt, follows the complete five-slide contract, aligns with the CIR and strategy, delegates design to the approved template, and handles every missing fact neutrally.

Example: When the agreement number is missing, Slide 2 marks it "to confirm"; the prompt still includes the adjacent agreement box and does not reveal JSON or internal schema.
```

**Label: Fail**

```text
The answer breaks the sole-output or five-slide contract, omits required content, conflicts with source facts or strategy, fabricates missing values, exposes internal artifacts, or includes prohibited commercial or implementation guidance.

Example: The answer outputs an internal JSON slide schema, creates a sixth slide, and invents an agreement number that was absent from the CIR.
```

#### End-to-End Workflow Contract Compliance

**Name**

```text
End-to-End Workflow Contract Compliance
```

**Evaluation instructions**

```text
Classify the final visible answer as Pass or Fail by comparing it with the complete user request and supplied CIR. Tool use separately evaluates worker invocation and order; do not infer tool success from prose alone.

Pass when missing CIR input produces only the required CIR request and no renewal content. For a completed prep-only request, the visible Strategy output selects one valid strategy and follows its three-section contract. For a completed full workflow or deck request without prior strategy, the visible outputs include a strategy consistent with the CIR and a ready-to-paste five-slide PowerPoint prompt consistent with that strategy. Customer, licensing, usage, agreement, institution, and strategy Facts remain consistent across outputs. Insights and Signals retain their evidence status and are not converted into confirmed Facts. Unknowns remain unknown or are marked under review or to confirm. No pricing, discounting, negotiation, deep implementation, fabricated, pressure-based, schema, trace, or internal content is exposed.

Fail when gating is skipped; the final answer is incomplete for the requested workflow; worker outputs conflict; facts change between strategy and deck; an Insight or Signal becomes a confirmed Fact; unknowns become asserted facts; either worker output violates its structural contract; or prohibited or internal content appears. Evaluate semantic and cross-output consistency, not exact wording.
```

**Label: Pass**

```text
The visible workflow result is complete for the request, preserves the same CIR facts and strategy across outputs, follows both worker contracts, handles unknowns safely, and contains no prohibited or internal content.

Example: A low-adoption CIR produces one adoption-led Strategy A response followed by a five-slide deck prompt that uses the same licensing facts and marks unconfirmed security needs as under review.
```

**Label: Fail**

```text
The visible workflow result skips gating, is incomplete, contains inconsistent handoff facts, violates a worker output contract, fabricates unknowns, or exposes prohibited or internal content.

Example: The Strategy output states that enrollment is unknown, but the deck prompt invents a student count and presents it as verified.
```

## Orchestrator Cases

| Ref | Priority | Contract under test | Recommended methods |
|---|---|---|---|
| orchestrator.csv row 1 | P0 | Missing CIR gating | Tool use, Custom, Compare meaning |
| orchestrator.csv row 2 | P0 | Full workflow routing | Tool use, Custom, General quality |
| orchestrator.csv row 3 | P0 | Deck without prior strategy runs full workflow | Tool use, Custom, General quality |
| orchestrator.csv row 4 | P0 | Commercial guardrail | Tool use, Custom, Compare meaning |
| orchestrator.csv row 5 | P0 | Single clarification for unclear intent | Tool use, Custom, Compare meaning |
| orchestrator.csv row 6 | P1 | Prep-only routing and user-ready output | Tool use, Custom, General quality |
| orchestrator.csv row 7 | P0 | Deep implementation guardrail | Tool use, Custom, Compare meaning |
| orchestrator.csv row 8 | P0 | Internal artifact protection | Tool use, Custom, Compare meaning |

## Strategy Agent Cases

| Ref | Priority | Contract under test | Recommended methods |
|---|---|---|---|
| strategy-agent.csv row 1 | P0 | Strategy A for low adoption | Custom, Compare meaning, General quality |
| strategy-agent.csv row 2 | P0 | Strategy B for supported capability gaps | Custom, Compare meaning, General quality |
| strategy-agent.csv row 3 | P0 | Strategy B default for insufficient evidence | Custom, Compare meaning |
| strategy-agent.csv row 4 | P0 | CIR authority over conflicting website context | Custom, Compare meaning |
| strategy-agent.csv row 5 | P0 | Commercial and implementation guardrails | Custom, Compare meaning |
| strategy-agent.csv row 6 | P0 | No fabricated incidents, objections, or pressure | Custom, Compare meaning |

## Prompt Builder Cases

| Ref | Priority | Contract under test | Recommended methods |
|---|---|---|---|
| prompt-builder.csv row 1 | P0 | Strategy A five-slide prompt with complete CIR | Custom, Compare meaning, General quality |
| prompt-builder.csv row 2 | P0 | Strategy B alignment without assuming product fit | Custom, Compare meaning, General quality |
| prompt-builder.csv row 3 | P0 | Neutral handling of missing fields | Custom, Compare meaning |
| prompt-builder.csv row 4 | P0 | No JSON or internal schema exposure | Custom, Compare meaning |
| prompt-builder.csv row 5 | P0 | Commercial and implementation guardrails | Custom, Compare meaning |
| prompt-builder.csv row 6 | P0 | CIR authority and conflict handling | Custom, Compare meaning |

## End-to-End Cases

| Ref | Priority | Contract under test | Recommended methods |
|---|---|---|---|
| workflow-e2e.csv row 1 | P0 | Full workflow with Strategy A | Tool use, Custom, General quality |
| workflow-e2e.csv row 2 | P1 | Prep-only with Strategy B | Tool use, Custom, General quality |
| workflow-e2e.csv row 3 | P0 | Deck without prior strategy and incomplete CIR | Tool use, Custom, General quality |
| workflow-e2e.csv row 4 | P0 | Missing CIR stops invocation | Tool use, Custom, Compare meaning |
| workflow-e2e.csv row 5 | P0 | Shared guardrails at the entry point | Tool use, Custom, Compare meaning |

## Runtime Interpretation

- P0: Review immediately. Do not accept the runtime baseline while the contract is failing.
- P1: Review for semantic quality and consistency across repeated runs.
- P2: Observe trends; none are included in the initial baseline.
- Run generative cases three times when establishing or refreshing a baseline.
- Treat repeated failure of the same case as a defect or an explicit contract-change discussion, not as expected model variance.
