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
