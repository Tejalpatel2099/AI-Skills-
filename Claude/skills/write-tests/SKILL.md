---
name: write-tests
description: Writes focused, meaningful unit and integration tests that match the project existing framework and conventions. Use whenever the user asks to add tests, write tests, improve coverage, or test a function or module.
---

> **Invoke in Claude Code:** type `/write-tests` (or just describe the task and Claude triggers it automatically). Install path: `~/.claude/skills/write-tests/SKILL.md`.

## Purpose
Write focused, meaningful tests that verify real behavior.

## When to use
The user asks to add or write tests, improve coverage, or test a specific function or module.

## Steps
1. Identify the unit under test and its public contract: inputs, outputs, and side effects.
2. Detect the project's existing test framework and conventions (file layout, naming, fixtures) and match them exactly.
3. Cover, at minimum: the happy path, edge cases (empty, null, boundary, very large), error paths, and any documented behavior.
4. Use clear arrange–act–assert structure, one concept per test, and descriptive names like `test_<thing>_<condition>_<expected>`.
5. Test observable behavior, not private implementation details.

## Output format
Test file(s) placed where the project keeps tests, runnable with the project's test command.

## Constraints
- Don't write tests that can never fail (e.g., asserting a mock returns what you told it to).
- Don't mock something you can use directly.
- If meaningful coverage gaps remain, list them explicitly rather than padding with trivial tests.

## Example
For `divide(a, b)`: assert normal division, assert `divide(5, 0)` raises the expected error, and assert behavior on negative and float inputs.
