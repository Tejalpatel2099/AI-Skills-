# 03 · LLM Concepts (Generation & Behavior)

## How an LLM produces text
It predicts the next token's probability distribution, picks one, appends it, and repeats (autoregression). A **KV cache** stores past attention keys/values so each new token doesn't recompute the whole sequence — essential for fast generation.

## Training stages
- **Pretraining** — self-supervised next-token prediction on huge corpora; learns general language.
- **Fine-tuning / instruction tuning** — adapt to follow instructions or a domain.
- **In-context learning** — no weight changes; the model learns from examples in the prompt.

## Prompting modes
- **Zero-shot** — task described, no examples.
- **One-shot / few-shot** — one or several worked examples in the prompt to steer format and behavior.

## Sampling controls
- **Temperature** — randomness. 0 = deterministic/greedy; higher = more diverse (and more errors). Note: temperature 0 is *consistent*, not *correct* — a confidently wrong answer at 0 is still wrong.
- **Top-k** — sample only from the k most likely tokens.
- **Top-p (nucleus)** — sample from the smallest set of tokens whose probabilities sum to p. Adapts to how confident the model is.

## Hallucination
The model produces fluent but false content, because it generates plausible text, not verified facts. It worsens when the needed knowledge is missing, outdated, or private. **Grounding** the model in retrieved sources (RAG) is the main mitigation.

## Context window & "lost in the middle"
Models attend best to the **start and end** of a long context and can neglect the middle. Put the most important instructions/context at the edges; don't assume buried text is used.

## Open vs. closed models
- **Open** (e.g., Llama) — self-host, customize, control data; you own the infra.
- **Closed** (e.g., GPT, Claude, Gemini) — best-in-class quality via API; less control, per-token cost.

## Hands-on
Write a script that calls one model API and shows how temperature and top-p change outputs on the same prompt.
