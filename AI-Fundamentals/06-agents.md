# 06 · Agents

## What makes something an "agent"
A plain LLM call maps input → output once. An **agent** can plan, choose **tools**, act, observe results, and loop until a goal is met. It has autonomy over *which* steps to take.

## ReAct loop (Reasoning + Acting)
The standard pattern: **Thought → Action → Observation**, repeated.
1. **Thought** — reason about what to do next.
2. **Action** — call a tool (search, calculator, API, code run).
3. **Observation** — read the tool's result.
4. Repeat until done, then answer.

## Tools / function calling
You expose functions with clear names, descriptions, and typed parameters. Good tool *descriptions* matter as much as good prompts — that's how the model decides when/how to call them.

## Single vs. multi-agent
- **Single-agent** — one loop with tools; simpler, cheaper, easier to debug.
- **Multi-agent** — specialized agents (planner, researcher, reviewer) collaborate; more capable but more tokens and more failure modes.

## Memory
- **Short-term** — the current conversation/context window.
- **Long-term** — external store (often vector-based) the agent retrieves from across sessions for personalization and continuity.

## Production concerns
**Guardrails** (validate inputs/outputs), **cost/token budgets**, a **human fallback** for low-confidence or high-stakes actions, and **loop limits** so a stuck agent can't run forever. Always design the failure path, not just the happy path.

## Hands-on
Build a small ReAct agent with two tools (e.g., web search + calculator) and a max-step limit.
