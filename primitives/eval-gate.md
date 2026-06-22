# Eval Gate Primitive

Use this before claiming a change is better.

## Purpose

Define how to decide whether a proposed AI-infra change improves, regresses, or
only clarifies the system.

## Inputs

- Candidate patch or PR packet
- Target subsystem
- Expected improvement
- Correctness tests
- Benchmarks or eval tasks
- Baseline result
- Risk budget

## Output

A pass, fail, neutral, or inconclusive eval decision.

## Principle

Tests protect correctness. Benchmarks measure systems behavior. LLM evals
measure task quality. Review outcomes measure maintainer fit. Do not collapse
these into one score unless you preserve the components.

## Eval Types

| Type | Use when | Examples |
|---|---|---|
| Correctness gate | behavior must not change incorrectly | unit tests, integration tests, golden outputs |
| Serving gate | latency or throughput may change | TTFT, TPOT, ITL, E2EL, tokens/sec |
| Memory gate | cache or model memory may change | peak GPU memory, KV cache utilization |
| Quality gate | generation or retrieval quality may change | exact match, task score, judge rubric |
| Operability gate | docs, errors, logs, metrics change | docs build, metric visibility, error clarity |
| Maintainer gate | contribution quality is the bottleneck | scope, review comments, CI, style |

## Decision Rules

- **Pass**: correctness holds and target metric improves or documentation/test
  value is clear.
- **Neutral**: no measurable improvement, but clarity or coverage improved.
- **Fail**: correctness breaks or a key metric regresses beyond the risk budget.
- **Inconclusive**: the available environment cannot measure the claim.

## Eval Record Format

```markdown
Change:
Claim:
Subsystem:

Baseline:
- command:
- result:

Candidate:
- command:
- result:

Decision: pass | neutral | fail | inconclusive

Why:
Regression risks:
Follow-up:
```

