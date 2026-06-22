# Agentic Contribution Kit

Design agentic open-source contributions before you ask an agent to code them.

This repository is a portable, Markdown-first kit for turning public GitHub
issues into responsible contribution packets. It is built for humans working
with coding agents across Codex, Claude Code, GitHub Copilot, Cursor, OpenCode,
and similar tools.

Most agent workflows optimize for "make a change." This kit optimizes for the
full open-source loop:

```text
issue triage -> repo loading -> scoped plan -> validated patch -> PR packet -> review loop -> evidence ledger
```

## Why This Exists

AI coding agents can generate patches quickly, but open-source contribution is
not just patch generation. A good contribution also needs:

- a non-duplicated issue
- maintainer-aware scope
- repo instruction and contribution-rule loading
- source-backed reasoning
- focused tests or validation
- a clear PR body
- careful review response
- public evidence that can be reused in a portfolio

The goal of this kit is to make that discipline repeatable.

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
  pr-packet.md          Build the branch, validation evidence, and PR body.
  review-loop.md        Respond to automated and maintainer review carefully.
  evidence-ledger.md    Convert public work into durable portfolio evidence.

examples/
  README.md
  contribution-packet-template.md

schemas/
  contribution-packet.schema.json
```

## Quickstart

1. Pick a public issue or PR candidate.
2. Run [issue triage](primitives/issue-triage.md).
3. If the candidate survives, run [repo load](primitives/repo-load.md).
4. Build the contribution using [PR packet](primitives/pr-packet.md).
5. Handle review with [review loop](primitives/review-loop.md).
6. Record the result in [evidence ledger](primitives/evidence-ledger.md).

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
- Scope before implementation.
- Maintainer signals before speed.
- Validation before PR.
- Review response before profile claims.
- Public evidence before polish.

## Status

Early template. The first milestone is to run this kit on three real AI-infra
contribution packets and refine the primitives from actual review outcomes.

