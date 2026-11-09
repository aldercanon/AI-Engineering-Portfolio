# Manual Runtime Workflow Tests

These tests cover conversation state and failure conditions that the two-column, single-turn CSV import cannot represent. Run them manually in Copilot Studio against the published runtime configuration.

## STATE-01: Deck After Prior Strategy

**Setup:** Start a new conversation with all connected agents available.

1. User: `Prepare my renewal conversation. Synthetic CIR: Synthetic K-12 District Alpha; public K-12; A3; active use 42%; EES expires 2027-06-30. All data is fictional.`
2. Confirm that the Orchestrator invokes Strategy and returns its complete output.
3. User: `Now create the customer-facing renewal deck from that strategy.`

**Pass:** The second turn invokes Prompt Builder only, passes the complete CIR and prior Strategy output, and returns only the ready-to-paste PowerPoint prompt.

## STATE-02: Strategy Refinement

**Setup:** Complete STATE-01 step 1.

1. User: `Refine the strategy to focus more on adoption barriers and stakeholder alignment.`

**Pass:** The Orchestrator re-invokes Strategy with the original CIR, prior output, and new constraint. It does not draft the refinement itself or invoke Prompt Builder.

## STATE-03: Deck Refinement

**Setup:** Complete a full workflow.

1. User: `Make the deck narrative more concise and emphasize collaborative next steps.`

**Pass:** The Orchestrator re-invokes Prompt Builder with the original CIR, complete Strategy output, prior deck prompt, and new constraint. The five-slide order remains unchanged.

## STATE-04: Strategy Change Requiring Downstream Refresh

**Setup:** Complete a full workflow using the low-adoption CIR.

1. User: `New validated evidence shows 86% core workload adoption and documented identity protection and data governance priorities. Update the strategy and deck.`

**Pass:** Strategy is invoked first with original context plus the new evidence, followed by Prompt Builder using the revised Strategy output. Facts from the superseded strategy do not remain in the deck.

## STATE-05: Worker Error And Retry

**Setup:** In a test environment, make the Strategy worker unavailable or use an approved runtime mechanism that produces an empty/error response.

1. User requests call preparation with a complete CIR.
2. Confirm the worker error response.
3. User: `Retry.`

**Pass:** The Orchestrator does not create missing strategy content. It reports that the Strategy agent encountered an issue and offers retry or input adjustment. On retry, it invokes the same worker with the same context.

## STATE-06: Prompt Builder Error And Retry

**Setup:** Complete Strategy output, then make Prompt Builder unavailable using an approved test-environment mechanism.

1. User requests the deck.
2. Confirm the worker error response.
3. User: `Retry.`

**Pass:** The Orchestrator does not create slide content. It reports the Prompt Builder issue and retries the same worker with the CIR and complete Strategy output.

## STATE-07: Output Pass-Through

**Setup:** Run prep-only and capture the connected Strategy agent output from runtime trace evidence.

**Pass:** The user-visible Strategy output is unchanged in substance and structure. The Orchestrator adds no strategy, summary, schema, trace, or internal commentary. Repeat for Prompt Builder.

## STATE-08: One-Time CIR Gate

**Setup:** Start a new conversation.

1. User asks for a strategy without a CIR.
2. Confirm the CIR request.
3. User repeats the strategy request without providing a CIR.

**Pass:** No worker is invoked and no strategy is generated. The agent remains waiting for the required CIR without inventing account context.

## PARTNER-01: Three-Program Cap And EDU Default

**Setup:** Use a synthetic CIR and an environment with the authorized incentives guide available to Strategy.

1. User requests a partner-program assessment and provides customer facts but no segment statement.
2. Inspect the Strategy response and observable knowledge calls.

**Pass:** Strategy treats the customer as EDU without researching or validating segment; returns no more than three distinct, ranked candidates; bases ranking only on customer criteria and supplied evidence; and gives one concise validation action per candidate. It does not include partner prerequisites, payment information, or an overflow list.

## PARTNER-02: User-Provided Count Inference

**Setup:** Use synthetic user-provided facts that support a transparent seat-count calculation, but do not state the total directly.

1. User asks for likely-fit partner programs and supplies the count components and their relationship.
2. Inspect the evidence and status for each candidate.

**Pass:** Strategy may calculate the count only from those user-provided facts, shows the calculation basis, labels the result inferred, and identifies validation needed. It does not treat the inferred count as confirmed or supplement the user's information with external data. User-provided figures may support an inference when the relationship is defensible.

## PARTNER-03: Explicit Segment Override And Partner Criteria

**Setup:** Use synthetic customer facts and an authorized guide. User explicitly states the account is not EDU.

1. User requests the partner-program shortlist and provides the explicit segment statement.
2. Inspect candidate selection and ranking.

**Pass:** Strategy uses the user's explicit segment without independent review. Partner prerequisites, partner location, specialization, performance, enrollment, and payment terms do not affect customer-fit ranking.

## PARTNER-04: Guide Unavailable

**Setup:** Use a test environment where Strategy cannot access the authorized incentives guide.

1. User requests the partner-program shortlist with a synthetic CIR.
2. Inspect the response and tool calls.

**Pass:** Strategy states that guide access is unavailable and does not invent program names, criteria, eligibility, or a ranked shortlist. It may state which customer facts need validation.

## PARTNER-05: Scoped Customer Exclusion

**Setup:** Use the authorized guide where an EDU exclusion applies to a specific program option, with other options governed by their own criteria. Do not copy the criteria into repository materials.

1. User requests a partner-program shortlist and supplies customer facts without stating segment.
2. Inspect the result against the guide in the secured runtime.

**Pass:** Strategy assumes EDU, applies the exclusion only to the explicitly excluded option, and does not generalize it to other sizes or programs. It ranks remaining candidates only by their own customer criteria and evidence.

## RESOURCES-01: Two Subsections And Separate Caps

**Setup:** Use synthetic customer facts with the authorized incentives guide connected and at least one evidenced Microsoft resource need.

1. User requests Available Resources and supplies facts that may support multiple Microsoft and partner-led options.
2. Inspect Section 3 headings, resource counts, evidence, and the Prompt Builder output if a deck is requested.

**Pass:** Available Resources has exactly two subsections, in order: Microsoft Resources and Partner-Led Resources. It returns no more than two total assessments/masterclasses and no more than three distinct partner-led programs; unsupported or unavailable items are not used to pad either list. Microsoft qualification follows existing thresholds. Partner ranking ignores partner prerequisites. Prompt Builder excludes partner-led names, rankings, fit evidence, and validation notes from slides and presenter notes.

## Evidence To Capture

For every run, record:

- Test ID and date
- Published agent version
- Environment
- Input summary
- Invoked tools or topics and invocation order
- Actual visible response
- Pass or fail
- Failure notes, owner, and target review date
