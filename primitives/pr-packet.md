# PR Packet Primitive

Use this when the candidate passed triage and the repo context is loaded.

## Purpose

Produce a reviewable contribution packet: branch, patch, validation evidence,
PR body, and follow-up notes.

## Inputs

- Issue triage decision
- Repo load note
- Local branch
- Minimal implementation scope
- Test and validation commands

## Output

A PR-ready packet, even if maintainers later decide that an issue comment or
no-go is the better public action.

## Packet Types

- PR submitted
- PR-ready branch
- Issue or minimal repro filed
- Source-backed review comment
- No-go log with evidence

## Checklist

- [ ] Branch name is scoped and readable.
- [ ] Diff only touches the agreed files.
- [ ] Existing user or maintainer changes were not reverted.
- [ ] Tests or docs validation were run.
- [ ] Known skipped validation is explained.
- [ ] PR body links the issue.
- [ ] PR body states what changed and how it was validated.
- [ ] AI assistance disclosure follows repo policy.
- [ ] Public story hook is recorded but not exaggerated.

## PR Body Template

```markdown
## Summary
- 

## Validation
- 

## Notes
- 

Fixes #
```

## Packet Record Format

```markdown
Packet:
- Type:
- Repo:
- Issue:
- Branch:
- PR:
- Scope:
- Files changed:
- Validation:
- Review status:
- Public story hook:
- Next follow-up:
```

