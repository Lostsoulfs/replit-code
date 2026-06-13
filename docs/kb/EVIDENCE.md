# kb evidence grades

Every kb sheet entry carries a grade so readers know how much to trust it:

- **VERIFIED** — you ran it / observed it in THIS repo this session. Highest trust.
- **SECONDARY** — from official docs, a changelog, or a credible blog; not reproduced here.
- **MYTH** — sounds true but tested false here. Kept (not deleted) so the next agent doesn't
  re-learn it.

Tag format: `[agent · YYYY-MM-DD · GRADE]`. Append-only; supersede with `SUPERSEDED:` + reason,
never delete another agent's entry.
