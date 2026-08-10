# Knowledge Governance

## Purpose
Define approved knowledge sources, source ranking, and maintenance ownership.

Synthetic files under `Evaluations/fixtures/` are test inputs, not approved knowledge sources. Do not upload them to Copilot Studio knowledge because retrieval could contaminate runtime evaluation results.

## Source Taxonomy
1. Customer-provided intelligence reports
2. Current agreement and licensing artifacts
3. Internal sales guidance documents
4. Compliance guidance materials
5. Public web verification sources (limited-use)

## Source-of-Truth Ranking
Use highest-priority available source when conflicts occur.

1. Customer Intelligence Report (authoritative for tenant usage and licensing context)
2. Current agreement artifacts
3. Internal guidance
4. Compliance reference
5. Public web verification

## Public Web Use Constraints
Public web data may be used only for high-level institution verification (type, size band, rural/urban context). It must not be used to infer tenant-specific usage, confidential plans, or contract specifics.

## Ownership and Freshness Cadence
1. Assign owner for each source set.
2. Review critical sources monthly.
3. Revalidate guidance sources before major prompt releases.
4. Archive superseded sources with version/date metadata.

## Change Control
Any source priority change requires:

1. Architecture doc update
2. Prompt impact review
3. Evaluation refresh
4. Release note entry

Evaluation fixture changes that do not alter runtime knowledge or source priority require evaluation documentation and evidence updates only.

