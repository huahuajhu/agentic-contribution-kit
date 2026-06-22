# Paper Delta Ingest Primitive

Use this when a new AI paper may change how you understand a repo, issue, eval,
or contribution opportunity.

## Purpose

Turn a paper into repo-specific contribution hypotheses, not generic notes.

## Inputs

- Paper URL or citation
- Abstract and key claims
- Method or mechanism
- Evaluation setup and metrics
- Limitations
- Target repository or subsystem
- Existing repo docs, issues, and tests

## Output

A paper delta note with claims, repo relevance, possible evals, and contribution
hypotheses.

## Stop Conditions

Stop before proposing implementation when:

- the paper claim is not tied to a repo surface
- the paper's eval setup cannot be approximated locally
- the method requires unavailable hardware, data, or private model weights
- the idea would be a research project rather than a bounded contribution
- the repo already has an active issue or PR covering the same idea

## Checklist

- [ ] Extracted the main problem.
- [ ] Extracted the mechanism, not just the result.
- [ ] Identified the metrics used in the paper.
- [ ] Identified the workloads, model sizes, and hardware assumptions.
- [ ] Listed limitations and failure cases.
- [ ] Mapped the claim to repo files, docs, tests, or benchmark surfaces.
- [ ] Proposed one small contribution packet.
- [ ] Proposed one eval gate for the packet.

## Paper Delta Format

```markdown
Paper:
Repo:
Subsystem:

Claim:
Mechanism:
Paper metrics:
Assumptions:
Limitations:

Repo relevance:
- 

Possible contribution packets:
- docs:
- test:
- benchmark:
- issue/repro:
- code:

Eval gate:
- correctness:
- performance:
- quality:
- regression risk:

Decision:
```

