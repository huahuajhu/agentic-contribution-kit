# Agentic Contribution Kit

Design AI-infra contributions before you ask an agent to code them.

This repository is a portable, Markdown-first kit for turning public AI
infrastructure issues into responsible, knowledge-backed contribution packets.
It is built for humans working with coding agents across Codex, Claude Code,
GitHub Copilot, Cursor, OpenCode, and similar tools.

Most agent workflows optimize for "make a change." This kit optimizes for a
harder loop:

```text
paper/repo knowledge -> issue triage -> scoped hypothesis -> eval gate -> PR packet -> review/reward loop
```

## Why This Exists

AI coding agents can generate patches quickly, but AI-infra contribution is not
just patch generation. A serious contribution also needs:

- a non-duplicated issue
- domain knowledge about LLM serving, training, evals, or agent frameworks
- maintainer-aware scope
- repo instruction and contribution-rule loading
- source-backed reasoning
- focused tests, benchmarks, or evals
- a clear PR body
- careful review response
- public evidence that can be reused in a portfolio

The goal of this kit is to make that discipline repeatable.

## What Makes This AI-Oriented

This is not a generic coding-agent team template. The intended differentiator is
an AI-infra knowledge and feedback layer:

1. **Repo-specific systems spine**: start with vLLM-style concepts such as KV
   cache, PagedAttention, scheduling, batching, TTFT, TPOT, ITL, E2EL,
   throughput, memory pressure, distributed serving, and benchmark design.
2. **Paper-to-repo ingestion**: turn new papers into claims, mechanisms,
   expected tradeoffs, affected repo surfaces, and small contribution
   hypotheses.
3. **Eval gate**: decide whether a patch makes an LLM system better or worse
   using correctness tests, serving metrics, quality evals, and regression
   budgets.
4. **Reward loop**: use packet outcomes as feedback. The first version is a
   reward-scored decision log; later versions can use bandits or RL to choose
   better triage, implementation, and review strategies.

The target is contribution intelligence for AI systems, not prompt automation.

## Who This Is For

- Developers using agents to contribute to serious open-source repositories.
- Maintainers who want contributors to arrive with better-scoped PRs.
- AI infrastructure learners building public evidence through real PRs.
- Agent-tooling builders who treat instructions, plans, and review loops as
  designed primitives.

## Kit Structure

```text
primitives/
  issue-triage.md       Decide whether an issue is worth touching.
  repo-load.md          Load repo rules, source surfaces, tests, and owners.
  paper-delta-ingest.md Turn new papers into repo-specific hypotheses.
  eval-gate.md          Check whether a change improves system behavior.
  reward-loop.md        Learn from packet outcomes and feedback signals.
  pr-packet.md          Build the branch, validation evidence, and PR body.
  review-loop.md        Respond to automated and maintainer review carefully.
  evidence-ledger.md    Convert public work into durable portfolio evidence.

domains/
  vllm-systems-spine.md LLM serving concepts and contribution surfaces.

examples/
  README.md
  contribution-packet-template.md

schemas/
  contribution-packet.schema.json
```

## Quickstart

1. Pick a public issue or PR candidate.
2. Load the relevant domain spine, starting with
   [vLLM systems](domains/vllm-systems-spine.md) for LLM serving work.
3. Run [issue triage](primitives/issue-triage.md).
4. If the candidate depends on new research, run
   [paper delta ingest](primitives/paper-delta-ingest.md).
5. If the candidate survives, run [repo load](primitives/repo-load.md).
6. Define the [eval gate](primitives/eval-gate.md).
7. Build the contribution using [PR packet](primitives/pr-packet.md).
8. Handle review with [review loop](primitives/review-loop.md).
9. Score the outcome with [reward loop](primitives/reward-loop.md).
10. Record the result in [evidence ledger](primitives/evidence-ledger.md).

Use [examples/contribution-packet-template.md](examples/contribution-packet-template.md)
as the working file for a new packet.

## Contribution Packet Definition

A contribution packet is one of:

- a submitted PR with validation evidence
- a PR-ready branch blocked by maintainer assignment or hardware
- a source-backed issue or minimal repro
- a useful review comment on an existing PR
- a no-go decision with evidence and a better next candidate

This matters because maintainers control merge timing, but contributors control
the quality of the packet.

## Design Principles

- Source before patch.
- Systems knowledge before agent action.
- Paper claims become repo hypotheses, not hype.
- Scope before implementation.
- Maintainer signals before speed.
- Validation before PR.
- Eval deltas before "better" claims.
- Review response before profile claims.
- Public evidence before polish.

## Starting References

- [vLLM PagedAttention paper](https://arxiv.org/abs/2309.06180) for KV-cache
  memory pressure and serving throughput.
- [vLLM metrics documentation](https://docs.vllm.ai/en/stable/design/metrics/)
  for server and request-level observability.
- [vLLM benchmark serve CLI](https://docs.vllm.ai/en/stable/cli/bench/serve/)
  for TTFT, TPOT, ITL, and E2EL measurement.
- [OpenAI Evals](https://github.com/openai/evals) for LLM system eval patterns.
- [DSPy](https://arxiv.org/abs/2310.03714) for self-improving language-model
  pipelines optimized against metrics.

## Status

Early template. The first milestone is to run this kit on three real AI-infra
contribution packets and refine the primitives from actual review outcomes,
benchmarks, and eval deltas.
