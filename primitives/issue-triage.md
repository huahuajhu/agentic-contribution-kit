# Issue Triage Primitive

Use this before asking an agent to implement anything.

## Purpose

Decide whether a public issue is open, useful, unclaimed, scoped, and worth a
contribution packet.

## Inputs

- Issue URL
- Repository URL
- Current issue comments
- Linked PRs and duplicate issues
- Labels, assignees, milestone, and maintainer guidance
- Local or remote source references related to the issue

## Output

A go, ask-first, watch, or no-go decision with evidence.

## Stop Conditions

Stop and do not start implementation when:

- an open PR already solves the issue
- the issue is assigned or socially claimed in comments
- maintainers asked for design discussion first
- the issue is too broad to finish in one focused packet
- the change would require credentials, private data, or hardware you do not have
- you cannot identify a meaningful validation path

## Checklist

- [ ] Issue is still open.
- [ ] No open linked PR already covers the scope.
- [ ] No recent claimant comment makes the work socially taken.
- [ ] Labels suggest contributions are welcome.
- [ ] Expected files or source surfaces are identifiable.
- [ ] The smallest useful scope fits in one PR or one review comment.
- [ ] Validation command or evidence path is known.
- [ ] The public story hook is specific and honest.

## Decision Format

```markdown
Decision: go | ask-first | watch | no-go

Candidate:
- Repo:
- Issue:
- Scope:
- Why useful:
- Duplicate check:
- Claimant check:
- Source surfaces:
- Validation path:
- Public story hook:
- Next action:
```

