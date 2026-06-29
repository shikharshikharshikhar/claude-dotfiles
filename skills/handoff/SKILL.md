---
name: handoff
description: Maintain cross-session project continuity. Use to write or update a project HANDOFF.md (progress + next steps for the next session), to "catch up" at the start of a session, or when wrapping up work on a multi-session coding project.
---

# Project continuity

You run long, multi-session projects across machines and lean on handoff docs ("read the
handoff doc", "based on all the work I've done on this project"). Keep one living source of truth
per project.

## Mode A — write/update HANDOFF.md  (default when wrapping up a work session)
Create/overwrite `HANDOFF.md` in the project root. **Update in place — do not append duplicates.**
Sections:
- **Goal** — what the project is for, in 1–2 lines.
- **Current state** — what works right now.
- **Next steps** — prioritized, highest-value-per-effort first; concrete and actionable.
- **Key files** — `path:line` pointers to the code that matters.
- **Decisions & constraints** — the *why* behind non-obvious choices
  (e.g. "don't feed the target's own market price into the model").
- **Gotchas / risk callouts** — what to watch when testing or deploying.
- **Run / test** — the exact commands to get it running (venv, dev servers, etc.).

Write it so a cold session can fully resume from this file alone.

## Mode B — catch up  (start of a session)
Read `HANDOFF.md` + `CLAUDE.md` + any relevant memory, then summarize where things stand and
propose the next 1–3 actions. A SessionStart hook auto-surfaces `HANDOFF.md`, so it may already be
in context — don't re-read it redundantly.

## CLAUDE.md vs HANDOFF.md
- `CLAUDE.md` = **stable** project facts (stack, conventions, how to run). Auto-loaded every
  session — create one per repo.
- `HANDOFF.md` = **evolving** progress + next-steps. Updated each session.

## Git convention
- Match the repo's existing branch-naming convention (e.g. `branch-<initials>-YYYYMMDD-feature`).
- On request: draft a commit message, list the risk callouts to verify in the dev/staging
  environment, then push.
