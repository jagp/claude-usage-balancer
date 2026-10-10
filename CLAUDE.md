# CLAUDE.md

Project memory for `claude-usage-balancer`.

## What this is

A tool that lets Claude users **queue non-time-critical commands** — high-value
ones, or fan-out workflows like Fable's — and run them **opportunistically against
appropriately-specific models**, so they spend their usage allotment efficiently
instead of wasting it when a session or context window ends before they get to it.

In short: a **usage balancer** that soaks up spare capacity with deferred,
model-routed work. Three pieces to build:

- **Queue** — durable list of deferred commands, each tagged with how capable a
  model it actually needs (its "specificity" / required tier).
- **Scheduler** — decides *when* to drain the queue, using otherwise-idle usage.
- **Model router** — sends each command to the least-capable model that can still
  do it well, so the strongest (scarcest) capacity isn't spent on cheap work.

## Stack & layout

- **Language:** <TBD — not chosen yet>
- **Layout:** <TBD as the code lands>
- `.claude/hooks/` — omnilog + ado hooks (see below). `tests/` — PowerShell suite.
  `docs/autologging.md` — the omnilog hook-schema reference.

## Commands

```
<build command>    # TBD
<test command>     powershell -File tests/run-all.ps1
<lint command>     trunk check   # via .trunk/ (self-installs; rough on Windows)
```

## Conventions

- <Naming / style rules specific to this project — TBD.>
- One feature per `feature/*` branch off `develop` (git-flow).
- Keep the changelog's `[Unreleased]` section current.

## Configuration tiers

1. **Local / machine-only** (never committed): secrets, machine paths, personal
   editor overrides, OS-global autocorrect. `.env`, `*.local.json`, `git config --local`.
2. **Project** (committed here): `.editorconfig`, `.gitattributes`, `.vscode/`, CI.
3. **Shared conventions** (in `dev-conventions`): defaults reused across all projects.

Rule of thumb: *personal* -> tier 1, *this-project-specific* -> tier 2,
*every-project* -> tier 3.

## Notes for Claude

- **Autologging is on.** Every tool call and response is appended to `omnilog.md`
  by the dev-strap hooks in `.claude/hooks/` (descriptions only — never command
  text or file contents; ASCII, <=78 chars). It's an append-only ledger; don't
  edit or backfill it.
