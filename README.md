# 🧰 AI-Skills

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Skills](https://img.shields.io/badge/skills-7-blue.svg)
![Format](https://img.shields.io/badge/format-Agent%20Skills-purple.svg)

A personal toolkit of reusable **AI agent skills** for everyday software development, plus **AI fundamentals** notes for interview prep. Skills are written in the open *Agent Skills* format, so the same files work in both **Claude Code** and **OpenAI Codex CLI** (and Cursor, Gemini CLI, GitHub Copilot).

> Maintained by [@Tejalpatel2099](https://github.com/Tejalpatel2099). Two things live here: agent skills you can install into your coding agent, and reference notes for AI/LLM interviews.

---

## 📂 Repository structure
```
AI-Skills/
├── Claude/                  # Skills for Claude Code  (invoke with /skill)
│   ├── README.md            #   install + usage
│   └── skills/
│       ├── code-review/SKILL.md
│       ├── debug/SKILL.md
│       ├── write-tests/SKILL.md
│       ├── commit-and-pr/SKILL.md
│       ├── refactor/SKILL.md
│       ├── document-code/SKILL.md
│       └── explain-code/SKILL.md
├── Codex/                   # Same skills for OpenAI Codex CLI  (invoke with $skill)
│   ├── README.md            #   install + usage
│   └── skills/
│       ├── code-review/
│       │   ├── SKILL.md
│       │   └── agents/openai.yaml   # optional Codex UI metadata
│       ├── debug/SKILL.md
│       ├── write-tests/SKILL.md
│       ├── commit-and-pr/SKILL.md
│       ├── refactor/SKILL.md
│       ├── document-code/SKILL.md
│       └── explain-code/SKILL.md
└── AI-Fundamentals/         # Interview-ready reference notes
    ├── README.md
    ├── 01-ml-fundamentals.md
    ├── 02-transformers.md
    ├── 03-llm-concepts.md
    ├── 04-rag.md
    ├── 05-prompting.md
    ├── 06-agents.md
    ├── 07-fine-tuning.md
    └── 08-evaluation.md
```

---

## 🧠 What is an "agent skill"?
A skill is just a **folder with a `SKILL.md` file** — YAML frontmatter (`name` + `description`) followed by markdown instructions:

```markdown
---
name: code-review
description: Reviews code for bugs, security, and style. Use when the user asks to review code or check a PR.
---

## Steps
1. ...
```

The agent reads only the `name` and `description` at startup (cheap), and loads the full body **only when the task matches** ("progressive disclosure"). This means you can keep many skills installed with almost no overhead. The format is an open standard, so one skill works across Claude Code, Codex CLI, Cursor, Gemini CLI, and GitHub Copilot. Agent-specific frontmatter (like Claude's `allowed-tools` or `hooks`) is safely ignored by agents that don't support it.

---

## 🛠️ The everyday-dev skills
| Skill | What it does | When it triggers |
|-------|--------------|------------------|
| **code-review** | Reviews a diff/file for bugs, security, and style — *report only, no edits* | "review this", "check my PR", "look over these changes" |
| **debug** | Finds the **root cause** from an error/stack trace, then suggests a regression test | "this is throwing", "why does this fail?", an error paste |
| **write-tests** | Writes meaningful tests that match your framework | "add tests", "improve coverage" |
| **commit-and-pr** | Conventional Commit messages + full PR descriptions from a diff | "write a commit message", "draft the PR" |
| **refactor** | Behavior-preserving cleanup, one safe step at a time | "clean this up", "reduce duplication" |
| **document-code** | Docstrings, READMEs, comments in the right convention | "document this", "add docstrings" |
| **explain-code** | Explains unfamiliar code at the right depth | "what does this do?", onboarding |

---

## 🚀 Quick start

### Claude Code
```bash
# personal (all projects)
cp -r Claude/skills/* ~/.claude/skills/
# then in Claude Code:  /code-review   (or just describe the task)
```

### OpenAI Codex CLI
```bash
# personal (all projects)
cp -r Codex/skills/* ~/.codex/skills/
# then in Codex:  $code-review   (or just describe the task)
```

Per-project installs (checked into a repo so teammates get them) use `.claude/skills/` and `.codex/skills/` respectively. Full details in [`Claude/README.md`](Claude/README.md) and [`Codex/README.md`](Codex/README.md).

---

## 📚 AI Fundamentals
Short, interview-ready notes covering ML basics, transformers/attention, LLM concepts, **RAG** (the highest-frequency 2026 interview topic), prompting, agents, fine-tuning, and evaluation. Start at [`AI-Fundamentals/README.md`](AI-Fundamentals/README.md).

**The one framework to memorize — RAG vs. fine-tuning vs. both:**
- **RAG** → knowledge that changes / is private / is large; cheap, transparent updates.
- **Fine-tuning** → change behavior, tone, format, or a narrow skill; baked into weights.
- **Both** → grounded facts *and* a consistent voice.

---

## ✍️ Add your own skill
1. `mkdir Claude/skills/my-skill` (and/or `Codex/skills/my-skill`).
2. Create `SKILL.md` with `name` + `description` frontmatter and numbered instructions.
3. Make the `description` specific and a little "pushy" with trigger words — that's what decides when the agent uses it.
4. Keep the body focused (one job, well done). Every line costs context tokens once loaded.
5. Copy into `~/.claude/skills/` or `~/.codex/skills/` and test by sending a prompt that should trigger it.

## 📄 License
MIT — use and adapt freely.
