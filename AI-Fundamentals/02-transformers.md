# 02 · Neural Nets & Transformers

Where app-builders get caught. Be able to explain attention out loud in 60 seconds.

## From neural nets to transformers
A neural net stacks layers of weighted sums + activations; **backpropagation** computes gradients so gradient descent can update weights. Transformers replaced RNNs/LSTMs because they process a whole sequence **in parallel** (no step-by-step recurrence) and handle long-range dependencies better.

## Self-attention (the core idea)
For each token, attention asks: "which other tokens matter for understanding me?" It computes a weighted blend of all tokens, where the weights come from similarity.
- **Query (Q)** — what this token is looking for.
- **Key (K)** — what each token offers.
- **Value (V)** — the actual content carried.
- Score = `softmax(Q·Kᵀ / √d) · V`. The `√d` keeps scores from exploding.

## Multi-head attention
Run several attention computations in parallel ("heads"), each learning different relationships (syntax, coreference, etc.), then concatenate. More perspectives at once.

## Positional encoding
Attention has no built-in notion of order (it sees a *set* of tokens). Positional encodings inject "where in the sequence" each token sits. Modern models often use **RoPE** (rotary position embedding), which rotates Q/K vectors so relative position falls out naturally and generalizes to longer sequences.

## Layer norm + residual connections
- **Residual (skip) connections** let gradients flow through deep stacks and let layers learn refinements.
- **Layer normalization** stabilizes training by normalizing activations.

## Tokenization
Text is split into **tokens** (sub-word units) before the model sees it.
- **BPE / WordPiece / SentencePiece** are common algorithms.
- Token count drives **cost** and **context-window** limits — roughly ~4 chars per token in English.

## Embeddings
Tokens (and whole texts) map to **dense vectors** that capture meaning. Similar meanings sit close together; similarity is measured with **cosine distance**. This is the foundation of semantic search and RAG.

## Hands-on
Implement scaled dot-product attention from scratch in NumPy or PyTorch — just the Q/K/V math.
