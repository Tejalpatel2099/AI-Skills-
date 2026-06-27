---
name: document-code
description: Writes docstrings, README sections, and useful inline comments in the right convention for the language. Use whenever the user asks to document code, add docstrings, or write or improve a README.
---

> **Invoke in Claude Code:** type `/document-code` (or just describe the task and Claude triggers it automatically). Install path: `~/.claude/skills/document-code/SKILL.md`.

## Purpose
Write clear documentation: docstrings, README sections, and useful inline comments.

## When to use
The user asks to document code, add docstrings, or write a README.

## Steps
1. Match the language's docstring convention — Google or NumPy style for Python, JSDoc/TSDoc for JS/TS, Javadoc for Java, etc.
2. For each public function or class write: a one-line summary, parameters (type + meaning), return value, errors raised, and a short example if usage isn't obvious.
3. Comment the *why*, not the *what*. Skip comments that just restate the code.
4. For a README include: title, what it does, install steps, a quickstart, a usage example, and configuration.

## Constraints
- Don't over-comment obvious code.
- Keep every example runnable and correct.
- Don't document private internals unless asked.

## Example
A `parse_config(path)` docstring states it reads a YAML file, returns a `Config`, raises `FileNotFoundError` if missing, and shows one line of example usage.
