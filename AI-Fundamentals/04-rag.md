# 04 · Retrieval-Augmented Generation (RAG) ⭐

The highest-frequency interview topic in 2026. Study this deepest.

## What it is
RAG pairs an LLM with an external knowledge source. At query time the system retrieves relevant text and feeds it to the model as context, so answers are grounded in real, up-to-date, or private data instead of only the model's frozen training. Analogy: an open-book exam.

## The pipeline
1. **Ingest** documents.
2. **Chunk** them into passages.
3. **Embed** each chunk into a vector.
4. **Store** vectors in a vector database (index).
5. **Retrieve** — embed the user query, find nearest chunks by similarity.
6. **(Re-rank)** the candidates for relevance.
7. **Generate** — pass query + top chunks to the LLM.

## Chunking
Splitting documents so retrieval is precise.
- **Too large** → retrieves irrelevant filler, wastes context, dilutes the answer.
- **Too small** → loses surrounding context, answers feel fragmented.
- Strategies: fixed-size, **semantic** (split on meaning), **recursive** (split by structure: sections → paragraphs → sentences), and **parent-child** (retrieve small, expand to the parent for context).

## Vector databases
Store embeddings and do fast nearest-neighbor search. Options: **Pinecone** (managed), **Weaviate**, **FAISS** (library), **pgvector** (Postgres extension — good when you already use Postgres). Choose on scale, hosting, and latency needs.

## Re-ranking
Initial retrieval (fast **bi-encoder** or keyword **BM25**) may return the right chunks in the wrong order. A **cross-encoder re-ranker** reads query+chunk together and reorders by true relevance. Bi-encoders pre-compute embeddings (fast, scalable); cross-encoders can't pre-compute (slower, more accurate) — so you retrieve many with the bi-encoder, then re-rank the top few with the cross-encoder.

## Hybrid search
Combine **keyword (BM25)** + **vector** search. Keyword catches exact terms/IDs/jargon; vectors catch paraphrases and synonyms. Together they beat either alone.

## Evaluating RAG
- **Faithfulness** — is the answer supported by the retrieved context (no hallucination)?
- **Answer relevancy** — does it address the user's question?
- **Context relevancy** — were the retrieved chunks actually relevant?
You need all of them: a faithful answer to the wrong question is still useless.

## Common failure modes
Hallucinating *despite* correct context (prompt/instruction issue), duplicate or redundant chunks, slow retrieval on large corpora, poor handling of domain jargon, and broken parsing of PDFs with tables/layout. Add **citations / source attribution** and **per-user access control** for production.

## RAG vs. fine-tuning
RAG = knowledge lives outside the model, easy/cheap to update, transparent. Fine-tuning = changes the model's behavior/tone/format, baked into weights, costlier to update. Use RAG for facts that change; fine-tune for style or narrow skills; combine for both.

## Hands-on
Build RAG over ~20 of your own docs (pgvector works). Add a re-ranker and measure faithfulness/relevancy before and after.
