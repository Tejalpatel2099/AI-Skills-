---
name: explain-code
description: Explains what unfamiliar code does at a depth matched to the reader. Use whenever the user asks what code does, to explain a function or file, or is onboarding to a new codebase.
---

> **Invoke in Claude Code:** type `/explain-code` (or just describe the task and Claude triggers it automatically). Install path: `~/.claude/skills/explain-code/SKILL.md`.

## Purpose
Explain what a piece of code does, at a depth matched to the reader.

## When to use
The user asks "what does this do", "explain this", or is trying to understand unfamiliar code.

## Steps
1. Open with a one-sentence summary of the code's overall purpose.
2. Walk the main flow in execution order. Name the key data structures and say why they're used.
3. Call out the non-obvious parts: tricky logic, side effects, hidden assumptions, and gotchas.
4. Note external dependencies and what could break if they change.
5. Calibrate depth to the asker — more fundamentals for a beginner, more nuance for an experienced dev.

## Constraints
- Lead with the big picture before going line by line.
- Don't restate trivial lines ("this increments i").
- If you notice a likely bug while explaining, flag it.

## Example
For a memoized Fibonacci function: summarize it as "computes Fibonacci with caching", explain the cache dict, then highlight that it mutates a default argument — a common bug.
