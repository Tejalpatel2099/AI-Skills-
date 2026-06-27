# 05 · Prompt Engineering

## Prompt anatomy
- **System prompt** — role, rules, output format, constraints. Most leverage lives here.
- **User prompt** — the actual request.
- **Context** — retrieved docs, examples, prior turns.

## Core techniques
- **Few-shot** — include worked examples to lock in format and behavior. Choose examples close to the real input.
- **Chain-of-thought (CoT)** — ask the model to reason step by step before answering. Helps multi-step reasoning; adds latency/cost and doesn't always help simple tasks.
- **Structured output** — ask for strict JSON (and validate it) when the result feeds code. Specify the schema and say "JSON only, no prose."

## Query transformation (used in RAG)
- **HyDE** — generate a hypothetical answer, embed *that* to retrieve (often matches documents better than the bare question).
- **Query decomposition** — break a complex question into sub-questions, retrieve for each.
- **Step-back prompting** — ask a more general question first to surface broader context.

## Practical rules
- Be specific; state the format and the constraints ("do NOT…").
- Put the most important instructions at the start or end (the middle gets neglected).
- One prompt = one job; chain prompts for multi-step tasks.

## Hands-on
Build a small harness that runs the same task across 3 prompt styles (zero-shot, few-shot, CoT) and logs the differences.
