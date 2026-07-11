# CLAUDE.md

Project memory for `claude-usage-balancer`.

## What this is

<One or two sentences: what the project does and who it's for.>

## Stack & layout

- **Language:** <language / runtime, with version>
- **Layout:** <key directories and what lives in each>

## Commands

```
<build command>
<test command>
<lint command>
```

## Conventions

- <Naming / style rules specific to this project.>
- One feature per `feature/*` branch off `develop` (git-flow).
- Keep the changelog's `[Unreleased]` section current.

## Configuration tiers

1. **Local / machine-only** (never committed): secrets, machine paths, personal
   editor overrides, OS-global autocorrect. `.env`, `*.local.json`, `git config --local`.
2. **Project** (committed here): `.editorconfig`, `.gitattributes`, `.vscode/`, CI.
3. **Shared conventions** (in `dev-conventions`): defaults reused across all projects.

Rule of thumb: *personal* â†’ tier 1, *this-project-specific* â†’ tier 2, *every-project* â†’ tier 3.

## Notes for Claude

- The user has an ergonomic typing need: silently interpret typos from intent;
  do not interrupt their flow to confirm spelling.

