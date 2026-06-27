# Contributing to AI-Skills

Thanks for your interest in improving this toolkit! Contributions of new
skills, fixes, and reference-note improvements are all welcome.

## Adding a new skill

1. Create the folder: `Claude/skills/my-skill/` (and/or `Codex/skills/my-skill/`).
2. Add a `SKILL.md` with YAML frontmatter:
   ```markdown
   ---
   name: my-skill
   description: One specific sentence with trigger words. Use when ...
   ---

   ## Steps
   1. ...
   ```
3. Keep the body focused on **one job**. Every line costs context tokens once loaded.
4. Make the `description` specific and trigger-word rich — it decides when the agent fires the skill.

## Style guidelines

- One skill = one folder = one `SKILL.md`.
- Prefer numbered, imperative steps over prose.
- Keep skills agent-agnostic where possible; put agent-specific keys (e.g. Claude's
  `allowed-tools`) only where needed — other agents safely ignore them.

## Submitting changes

1. Fork the repo and create a feature branch.
2. Make your change with a clear, conventional commit message.
3. Open a pull request describing **what** changed and **why**.
4. Test the skill by sending a prompt that should trigger it before submitting.

## Reporting issues

Found a bug or have an idea? Open an issue with a short, reproducible description.
