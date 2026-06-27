---
name: refactor
description: Improves the structure of existing code without changing its behavior. Use whenever the user asks to refactor, clean up, simplify, dedupe, or reduce complexity.
---

> **Invoke in Claude Code:** type `/refactor` (or just describe the task and Claude triggers it automatically). Install path: `~/.claude/skills/refactor/SKILL.md`.

## Purpose
Improve the structure of existing code without changing its behavior.

## When to use
The user asks to refactor, clean up, simplify, or reduce duplication.

## Steps
1. Confirm tests exist for the code. If they don't, write characterization tests first — never refactor blind.
2. Identify the specific smell: duplication, an over-long function, deep nesting, unclear names, or tight coupling.
3. Make one small, behavior-preserving change at a time (extract function, rename, invert a guard clause, dedupe).
4. Keep the public interface stable unless the user asked otherwise.
5. After each step the code must still compile and pass its tests.

## Constraints
- Behavior must not change. Same inputs produce same outputs and side effects.
- Don't smuggle in new features or bug fixes — those are separate changes.
- If a cleaner design genuinely requires a behavior change, stop and flag it rather than doing it silently.

## Example
Replace three near-identical validation blocks with one `validate(field, rules)` helper, running tests after the extraction to confirm nothing changed.
