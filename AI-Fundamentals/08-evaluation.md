# 08 · Evaluation & Production Awareness

Knowing the vocabulary here sets you apart at the new-grad level.

## Why eval is hard
There's rarely one right answer for generated text, so you need **layered** evaluation, not a single number.

## The layers
1. **Automated metrics** (fast, cheap, continuous)
   - Task metrics: accuracy/F1 for classification, exact match for structured output.
   - Reference metrics: BLEU/ROUGE (overlap with a reference), semantic similarity, **perplexity** (how "surprised" the model is — lower is more fluent, not necessarily more correct).
2. **LLM-as-judge** — a stronger model scores outputs on dimensions like factual accuracy, relevance, completeness, and harmlessness. Scalable; watch for the judge's own bias.
3. **Human evaluation** — the gold standard; expensive, so used periodically. Side-by-side A/B comparisons are common.

## Production monitoring
- **Latency** and **throughput** — is it fast enough at load?
- **Drift** — live inputs shift away from what the model handles well; quality degrades silently. Monitor and retrain.
- **Cost / token budget** — track tokens per request; pick the cheapest model that passes eval.

## Serving vocabulary (be able to name these)
- **Batching / continuous batching** — group requests to use the GPU efficiently without blowing latency.
- **KV-cache reuse** — avoid recomputing attention for past tokens.
- **Streaming** — send tokens as they're generated for a responsive UX.

## Hands-on
Write an eval script that uses LLM-as-judge to score outputs from two prompts on ~10 examples and reports which wins.
