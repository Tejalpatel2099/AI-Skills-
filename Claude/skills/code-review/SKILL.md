---
name: code-review
description: Reviews code changes for bugs, security vulnerabilities, and style issues without modifying them. Use whenever the user asks to review code, check a pull request or diff, look over changes before merging, or find issues — even if they do not literally say "review".
---

> **Invoke in Claude Code:** type `/code-review` (or just describe the task and Claude triggers it automatically). Install path: `~/.claude/skills/code-review/SKILL.md`.

## Purpose
Review code for correctness, security, and maintainability and report findings — without changing the code.

## When to use
The user asks to review code, check a pull request or diff, or find issues before merging.

## Steps
1. Read the target. For a diff, focus on changed lines plus their immediate context, not the whole file.
2. Check in this priority order:
   1. **Correctness / logic** — off-by-one errors, null/undefined handling, unhandled edge cases, race conditions, incorrect comparisons.
   2. **Security** — injection (SQL, command, XSS), missing authentication/authorization, secrets committed in code, unsafe deserialization, path traversal.
   3. **Error handling** — swallowed exceptions, missing input validation, unchecked return values.
   4. **Performance** — N+1 queries, work inside hot loops, blocking calls on the request path, needless allocations.
   5. **Maintainability** — unclear names, duplication, dead code, missing or weak tests.
3. For every finding report: `file:line`, a severity (`blocker` / `major` / `minor` / `nit`), the concrete problem, and a suggested fix.

## Output format
Group findings by severity, most severe first. End with a one-line verdict: `approve`, `approve with nits`, or `request changes`.

## Constraints
- Do **not** modify code — report only.
- Be specific: "possible SQL injection at line 42 via a string-concatenated query" beats "check security".
- If you lack context to judge something, say so instead of guessing.

## Example
Input: a diff that adds `query = "SELECT * FROM users WHERE id = " + userId`.
Output: `major — auth.py:42 — SQL injection: userId is concatenated into the query. Use a parameterized query: cursor.execute("... WHERE id = %s", (userId,)).`
