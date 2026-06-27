# Codex CLI Skills

The same seven everyday-developer skills, packaged for OpenAI Codex CLI. The Agent Skills format is shared, so these `SKILL.md` files are nearly identical to the Claude versions — only the install path and invocation differ.

## What a skill is
A folder with a `SKILL.md` (`name` + `description` + markdown instructions). Codex uses **progressive disclosure**: it keeps each skill's name/description/path in context (capped at ~2% of the context window) and loads the full instructions only when it picks the skill.

## Install
**Personal:**
```bash
cp -r Codex/skills/* ~/.codex/skills/
```
**Per-project (checked into the repo):**
```bash
mkdir -p .codex/skills && cp -r Codex/skills/* .codex/skills/
```
Codex also scans `.agents/skills` walking up from your working directory to the repo root. It detects changes automatically; restart Codex if an update doesn't appear.

## Use
- **Automatic (implicit):** describe the task; Codex matches it to a skill by description. Because matching depends on the description, the trigger words are front-loaded in each one.
- **Explicit:** type `$code-review`, `$debug`, etc., or run `/skills` to browse.

## Optional `agents/openai.yaml`
Codex reads an optional `agents/openai.yaml` inside a skill folder for UI metadata, invocation policy, and tool dependencies. See `skills/code-review/agents/openai.yaml` for a worked example. Claude and other agents ignore this file.

## The skills
Same set as the Claude folder: `code-review`, `debug`, `write-tests`, `commit-and-pr`, `refactor`, `document-code`, `explain-code`.

## Note
Codex ships a few built-in skills (`$skill-creator`, `$skill-installer`) and a curated set "inspired by popular workflows at OpenAI." These custom skills follow the same pattern and sit alongside them.
