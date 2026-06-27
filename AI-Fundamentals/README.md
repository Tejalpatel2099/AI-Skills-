# AI Fundamentals

Interview-ready reference notes for AI/LLM concepts, aimed at the new-grad / early-career SWE bar. Each file is short on purpose — enough to explain the concept out loud in an interview and to anchor a small hands-on project.

These pair with the skill files in `../Claude` and `../Codex`: the skills are *how* you work with an AI coding agent day to day; these notes are *what* the underlying systems are.

## Contents
| # | File | Covers | Why it matters in interviews |
|---|------|--------|------------------------------|
| 01 | [ML fundamentals](01-ml-fundamentals.md) | gradient descent, loss, overfitting, metrics | The "junior-bar" questions, asked directly |
| 02 | [Transformers](02-transformers.md) | attention, Q/K/V, positional encoding, tokenization | Tests whether you know internals vs. just APIs |
| 03 | [LLM concepts](03-llm-concepts.md) | sampling, temperature, few-shot, hallucination | Core vocabulary for any LLM role |
| 04 | [RAG](04-rag.md) | retriever + generator, chunking, vector DBs, re-ranking | **Highest-frequency topic** in 2026 loops |
| 05 | [Prompting](05-prompting.md) | system/user prompts, chain-of-thought, query transforms | Practical, shows up in take-homes |
| 06 | [Agents](06-agents.md) | ReAct loop, tools, memory, guardrails | Increasingly standard, esp. at agent-first companies |
| 07 | [Fine-tuning](07-fine-tuning.md) | RAG vs. fine-tune, LoRA/QLoRA, RLHF vs. DPO | Know the *why*, not the GPU bill |
| 08 | [Evaluation](08-evaluation.md) | metrics, LLM-as-judge, monitoring, drift | What separates "read about it" from "shipped it" |

## The one framework to memorize
**RAG vs. fine-tuning vs. both** is reported as the single most-asked LLM question in 2026. Interviewers want a *decision rule*, not a definition:
- **RAG** when knowledge changes often, is large, or is private/company-specific, and you want cheap, transparent updates.
- **Fine-tuning** when you need to change behavior, tone, format, or teach a narrow skill — knowledge baked into weights.
- **Both** when you need grounded facts *and* a consistent voice/format.

## Practice question banks
- `github.com/amitshekhariitbhu/ai-engineering-interview-questions` — LLM, RAG, MCP, agents, fine-tuning, quantization
- `github.com/KalyanKS-NLP/RAG-Interview-Questions-and-Answers-Hub` — 100+ RAG questions
