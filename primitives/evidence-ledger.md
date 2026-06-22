# Evidence Ledger Primitive

Use this after each public contribution packet.

## Purpose

Convert contribution work into durable public evidence without overstating the
result.

## Inputs

- PR, issue, or review link
- Packet record
- Validation result
- Review or merge status
- Lessons learned

## Output

A profile-ready summary, resume bullet candidate, and next-action note.

## Status Language

Use precise language:

- "Merged PR" only after merge.
- "Open PR" while review is pending.
- "Review-ready PR" when the branch and PR are ready but not merged.
- "Source-backed review" for useful review comments.
- "Repro filed" for issue evidence.
- "No-go logged" when the useful outcome was avoiding duplicate or low-value work.

## Checklist

- [ ] Public link is recorded.
- [ ] Status is accurate today.
- [ ] Summary names the system surface, not just the file.
- [ ] Validation is included.
- [ ] Reviewer-feedback loop is noted if relevant.
- [ ] Resume/profile wording does not imply maintainer approval before merge.
- [ ] Next follow-up is clear.

## Ledger Format

```markdown
## YYYY-MM-DD | repo | packet title

Status:
Link:
System surface:
What changed:
Validation:
Review state:
Public story:
Resume bullet candidate:
Next follow-up:
```

