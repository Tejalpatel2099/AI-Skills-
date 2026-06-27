---
name: commit-and-pr
description: Generates Conventional Commit messages and full pull-request descriptions from a diff. Use whenever the user asks for a commit message, a PR description, release notes, or a summary of what changed.
---

> **Invoke in Claude Code:** type `/commit-and-pr` (or just describe the task and Claude triggers it automatically). Install path: `~/.claude/skills/commit-and-pr/SKILL.md`.

## Purpose
Turn a diff into a clear commit message and/or pull-request description.

## When to use
The user asks for a commit message, a PR description, or a summary of what changed.

## Steps
1. Read the actual diff (for example `git diff --staged`). Base everything on what the diff really does.
2. **Commit message** — follow Conventional Commits:
   - Subject: `type(scope): summary` in the imperative mood, ≤ 50 characters.
   - Blank line, then a body explaining *what changed and why* (not how), wrapped at ~72 characters.
   - Types: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`, `perf`.
3. **PR description** — use sections: `## What`, `## Why`, `## How`, `## Testing`, `## Risks / rollout`. Link related issues.

## Constraints
- Describe only changes present in the diff — never invent changes.
- Flag anything risky: database migrations, breaking API changes, or secrets.
- Keep the subject line a summary, not a list.

## Example
Subject: `fix(auth): reject expired tokens before DB lookup`. Body: explains the prior behavior leaked a query on expired tokens and the fix short-circuits earlier.
