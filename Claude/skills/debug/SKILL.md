---
name: debug
description: Systematically diagnoses and fixes the root cause of a bug from an error message, stack trace, or failing test. Use whenever the user shares an error, a traceback, a crash, or says code "is not working" or "works locally but not in prod".
---

> **Invoke in Claude Code:** type `/debug` (or just describe the task and Claude triggers it automatically). Install path: `~/.claude/skills/debug/SKILL.md`.

## Purpose
Systematically find and fix the root cause of a bug, given an error, stack trace, or wrong behavior.

## When to use
The user shares an error message, a stack trace, a failing test, or says something "works in X but not Y".

## Steps
1. **Reproduce.** Identify the exact command/input that triggers the bug. If repro steps are unclear, ask for them before guessing.
2. **Locate.** Read the stack trace from the bottom up to the first line in the user's own code; that is usually where to start.
3. **Hypothesize.** State an explicit hypothesis for the cause before changing anything.
4. **Isolate.** Narrow to a minimal failing case. Add targeted logging or assertions if the cause isn't visible.
5. **Confirm the root cause** — not just the symptom.
6. **Fix.** Propose the smallest change that addresses the root cause. Explain why it works and what it does not cover.
7. **Prevent.** Suggest a regression test that would have caught this bug.

## Constraints
- Don't patch the symptom while leaving the root cause in place.
- Don't touch unrelated code.
- State your assumptions explicitly so the user can correct them.

## Example
Given `IndexError: list index out of range` on `items[i+1]`, hypothesize an off-by-one at the loop boundary, confirm `i` reaches `len(items)-1`, fix the range bound, and add a test for the single-element list case.
