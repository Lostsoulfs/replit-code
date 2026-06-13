# 0018. Portable docs/kb machine-to-machine knowledge base

- **Status:** Accepted
- **Date:** 2026-06-13

## Context

Tool facts for this repo's stack (PixiJS v8, Vite, Vitest, WebAudio, ESLint) and hard-won
gotchas have lived only in `docs/LEARNINGS.md`, mixed with project-specific lessons. That
conflates two different things — durable _tool_ knowledge (reusable, stack-scoped) and
_project_ gotchas (this repo's history) — and offers no per-agent continuity across sessions.
codex-speed-test solved this with a portable `docs/kb/` knowledge base (its ADR-0018):
version-pinned, example-heavy crib sheets plus per-agent journals, explicitly designed to be
copied between repos. A cross-repo governance rollout brought the contract here.

## Decision

Adopt the portable `docs/kb/` contract:

- `INDEX.md` (read-before / write-after contract + catalog), `TEMPLATE.md`, `EVIDENCE.md`
  (VERIFIED / SECONDARY / MYTH grades), and per-agent journals under `journal/`.
- kb = the **stack** (tool facts, graded, append-only). `docs/adr/` keeps project decisions;
  `docs/LEARNINGS.md` keeps project gotchas. Working Agreement #9's distillation pass feeds
  verified tool-facts from LEARNINGS into kb.
- The catalog starts **empty**: sheets are created only as facts are verified from real runs —
  no fabricated content, and no importing another repo's stack sheets.

## Consequences

- Easier: per-tool knowledge is found fast (progressive disclosure), and agents get
  cross-session continuity via their own journal.
- Harder / cost: one more place to keep honest — the `audit-drift` checks and WA #9 distill
  rule apply to kb too; stale or fabricated entries are a drift finding.
- Follow-up: seed sheets opportunistically when a real gotcha appears; revisit if the catalog
  stays empty long enough to question the overhead.

## Alternatives considered

- **Keep everything in `docs/LEARNINGS.md`** — why not: conflates tool facts with project
  history, no per-agent continuity, and LEARNINGS already triggers the `learnings-distill-due`
  nag past ~500 lines.
- **Skip the kb entirely (as lostsouls-game did, ADR-0005)** — why not: lostsouls is a
  deliberately light hybrid; this repo runs the full agent apparatus (auditor/explorer/planner)
  and a fast-moving Pixi/Vite stack where docs-in-context demonstrably helps.
