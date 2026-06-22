# Reward Loop Primitive

Use this after a packet, review, benchmark, or eval result.

## Purpose

Turn contribution outcomes into feedback that improves future agent decisions.
This is the RL-shaped part of the kit, but the first version is deliberately
simple: a transparent reward log before any automated learner.

## What RL Means Here

The reward is not "the agent wrote code." The reward is whether the contribution
made the target system or contribution process better.

Potential future learners:

- contextual bandit for selecting issues or packet types
- policy search over triage and implementation strategies
- reward model for ranking candidate patches
- offline RL from packet logs after enough examples exist

Do not use RL to replace tests, benchmarks, or maintainer review. Use it to
choose better actions based on those signals.

## Reward Components

| Component | Range | Meaning |
|---|---:|---|
| Correctness | -3..3 | Tests pass, behavior is preserved, bugs are fixed. |
| Systems metric | -3..3 | Latency, throughput, memory, or quality moved as expected. |
| Maintainer fit | -2..2 | Scope, style, reviewability, and responsiveness. |
| Learning value | 0..2 | New domain knowledge captured for future work. |
| Public evidence | 0..2 | Useful PR, issue, review, benchmark, or no-go record. |
| Risk penalty | -5..0 | Broken CI, broad scope, unsupported claim, or misleading profile story. |

## Reward Record Format

```markdown
Packet:
Repo:
Subsystem:
Action:

Signals:
- tests:
- benchmark/eval:
- review:
- merge/status:
- knowledge captured:

Reward:
- correctness:
- systems_metric:
- maintainer_fit:
- learning_value:
- public_evidence:
- risk_penalty:
- total:

Policy update:
- do more:
- do less:
- next experiment:
```

## Minimum Viable Loop

1. Score every packet manually.
2. Compare predicted value against actual outcome.
3. Keep examples where the agent chose poorly.
4. Use the examples to update triage, repo-load, eval-gate, and PR-packet
   prompts.
5. Only automate after at least 20 scored packets.

