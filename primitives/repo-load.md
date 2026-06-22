# Repo Load Primitive

Use this after issue triage passes and before editing files.

## Purpose

Force the human and agent to learn the repository's rules, architecture, and
validation surface before making a patch.

## Inputs

- Repository checkout
- Issue or PR candidate
- Contribution docs
- Agent instruction files
- Test and lint commands
- Relevant source files
- Existing examples or similar fixes

## Output

A loaded-context note that names the rules, files, commands, and constraints
that will govern the contribution.

## Stop Conditions

Stop and ask or switch candidates when:

- contribution rules forbid the planned scope
- required tests cannot be identified
- repo-specific instructions conflict with the proposed edit
- local source no longer matches the issue
- similar files reveal the planned patch is inconsistent with repo style

## Files To Search

- `AGENTS.md`
- `.github/copilot-instructions.md`
- `.github/instructions/**`
- `CONTRIBUTING.md`
- `README.md`
- docs contribution guides
- test, lint, and formatting config
- files named in the issue
- recent PRs touching the same area

## Checklist

- [ ] Read root instructions.
- [ ] Read area-specific instructions.
- [ ] Read contribution and PR rules.
- [ ] Identified expected changed files.
- [ ] Found nearest tests or validation commands.
- [ ] Found existing patterns to match.
- [ ] Recorded constraints and reviewer expectations.

## Loaded Context Format

```markdown
Repo:
Candidate:

Rules read:
- 

Relevant files:
- 

Existing patterns:
- 

Validation:
- 

Constraints:
- 

Implementation boundary:
- 
```

