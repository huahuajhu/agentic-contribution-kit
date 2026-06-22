# Review Loop Primitive

Use this after automated review, maintainer review, CI, or user feedback.

## Purpose

Respond to review carefully. The goal is not to accept every suggestion, but to
separate valid feedback from suggestions that conflict with repo rules, scope,
or source truth.

## Inputs

- PR URL
- Review comments
- CI results
- Current diff
- Repo instructions
- Relevant source and docs

## Output

Resolved review threads, amended commits or follow-up comments, and an updated
packet record.

## Stop Conditions

Stop and ask before changing code when:

- reviewer feedback conflicts with repo instructions
- the requested change expands scope materially
- a maintainer asks for a design decision
- CI failure requires unavailable credentials or hardware
- the fix would touch unrelated files

## Checklist

- [ ] Read each comment in context.
- [ ] Classify each comment as apply, discuss, defer, or reject-with-rationale.
- [ ] Re-read repo rules if the comment concerns docs, style, tests, or links.
- [ ] Apply valid comments in the smallest diff.
- [ ] Rerun relevant validation.
- [ ] Reply with concise evidence for comments not applied.
- [ ] Resolve threads only after the response or fix is complete.
- [ ] Update the packet record with commit, validation, and review status.

## Comment Decision Format

```markdown
Comment:
- Link:
- Classification: apply | discuss | defer | reject-with-rationale
- Reason:
- Action:
- Validation:
```

