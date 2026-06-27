# Claude Code Skills

Seven everyday-developer skills in the open Agent Skills format, ready to drop into Claude Code.

## What a skill is
A folder with a `SKILL.md` file: YAML frontmatter (`name` + `description`) plus markdown instructions. At startup Claude reads only each skill's name and description (~100 tokens each). The full body loads **only when Claude decides the skill is relevant** — so you can keep many installed without slowing anything down.

## Install
**Personal (all your projects):**
```bash
cp -r Claude/skills/* ~/.claude/skills/
```
**Per-project (checked into a repo, shared with teammates):**
```bash
mkdir -p .claude/skills && cp -r Claude/skills/* .claude/skills/
```
Restart Claude Code (or start a new session) to pick them up.

## Use
- **Automatic:** just describe the task — "review this diff", "why is this test failing?" — and Claude triggers the matching skill.
- **Explicit:** type `/code-review`, `/debug`, `/write-tests`, etc.

## The skills
| Skill | What it does |
|-------|--------------|
| `code-review` | Reviews a diff/file for bugs, security, and style — report only |
| `debug` | Root-cause a bug from an error or stack trace, then suggest a regression test |
| `write-tests` | Writes meaningful tests matching your framework |
| `commit-and-pr` | Conventional Commit messages + PR descriptions from a diff |
| `refactor` | Behavior-preserving cleanup, one safe step at a time |
| `document-code` | Docstrings, READMEs, and useful comments in the right convention |
| `explain-code` | Explains unfamiliar code at the right depth |

## Claude-only frontmatter (optional)
The portable fields are `name` and `description`. Claude Code also supports extras that other agents safely ignore: `allowed-tools`, `disable-model-invocation`, `context: fork` (run as an isolated subagent), and `hooks`. Add them only when you need them.
