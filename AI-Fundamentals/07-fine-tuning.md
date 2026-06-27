# 07 · Fine-Tuning (Concepts)

Know *why* and *when*, not the GPU bill.

## When fine-tuning beats RAG
Use fine-tuning to change **behavior, tone, format, or a narrow skill** — things you want baked into the model. Use RAG for **knowledge that changes or is private**. They're complementary, not competitors.

## PEFT (Parameter-Efficient Fine-Tuning)
Full fine-tuning updates all weights — expensive. PEFT updates a small number instead:
- **LoRA** — inserts small low-rank adapter matrices; trains those, freezes the base model. Far cheaper, fast to swap.
- **QLoRA** — LoRA on top of a **quantized** (lower-precision) base model, so it fits on much smaller hardware.

## Instruction tuning
Fine-tuning on (instruction, response) pairs so a base model learns to follow instructions — the step that turns a raw next-token predictor into a usable assistant.

## Alignment: RLHF vs. DPO
- **RLHF** — train a reward model from human preferences, then optimize the LLM against it (PPO). Powerful but complex.
- **DPO (Direct Preference Optimization)** — optimizes directly on preference pairs, no separate reward model. Simpler and more stable; now widely used. (GRPO is a newer variant used in some reasoning models.)

## Quantization
Reduce numerical precision (e.g., 16-bit → 4-bit) to cut memory and speed up inference, accepting a small accuracy loss. Key for running models on limited or edge hardware.

## Hands-on
Run one LoRA fine-tune on a small open model (Hugging Face) over a toy dataset — even a tiny run teaches the workflow.
