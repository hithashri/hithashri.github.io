---
title: MES RAG Chatbot, Vector Search and Retrieval Architecture
permalink: /projects/mes-rag-chatbot/
---

<a class="back-link" href="/projects.html">← Projects</a>

# MES RAG Chatbot: Vector Search and Retrieval Architecture

<div class="project-links">
  <a href="https://github.com/hithashri/mes_rag_chatbot" class="btn btn-primary" target="_blank" rel="noopener">GitHub ↗</a>
</div>

## Executive Overview

Built a fully functional RAG chatbot for a manufacturing use case, implementing the complete vector search pipeline from document ingestion through semantic retrieval to grounded LLM generation, with a human-in-the-loop knowledge base updater for handling out-of-distribution queries. Built independently to explore and implement the retrieval architecture underlying production RAG systems.

<!-- ## Motivation

At Bosch, I built the production breakdown recommendation system that served technicians on the factory floor, but that project operated within proprietary infrastructure where the vector search, embedding pipeline, and retrieval logic were abstracted behind enterprise tooling. I did not get to build the RAG internals from scratch: choosing the embedding model, configuring the vector store, tuning retrieval thresholds, or designing fallback behaviour when the system encounters something outside its training distribution.

I wanted to understand those mechanics at the implementation level: how chunking strategy affects retrieval quality, where cosine distance thresholds should sit to balance recall and hallucination risk, and what happens architecturally when a RAG system needs to extend its own knowledge base at runtime. This project was built to answer those questions hands-on. -->

## Problem Statement

How do you build a RAG system that knows when it does not know the answer, and what happens when it encounters a query outside its knowledge base?

## Solution Design

- Ingested both structured (CSV error codes) and unstructured (equipment manuals) data into a persistent local vector store using sentence-transformer embeddings.
- Implemented semantic retrieval with a tunable cosine distance fallback threshold to detect low-confidence retrievals before they reach the generation layer.
- Constrained LLM generation strictly to retrieved context to prevent hallucination.
- Built a human-in-the-loop updater that triggers when retrieval confidence is low, allowing operators to extend the knowledge base interactively and automatically rebuild the vector index.

## System Design and Architecture

- **Ingestion layer (ingest.py):** Reads structured error code records from CSV and unstructured equipment manual text. Applies paragraph-level chunking on blank line boundaries. Embeds all documents using all-MiniLM-L6-v2 (384-dimensional vectors). Stores in a ChromaDB persistent collection with HNSW indexing and cosine similarity.
- **Retrieval layer (retriever.py):** Embeds incoming query using the same sentence-transformer model. Queries ChromaDB for top-3 most semantically similar chunks. Applies cosine distance fallback threshold of 0.4; retrievals above this threshold trigger the fallback path. Returns results alongside a fallback_needed flag.
- **Generation layer (generator.py):** Orchestrates the full pipeline. On successful retrieval, builds a grounded prompt with retrieved context and calls OpenAI gpt-4o-mini at temperature 0.2 with strict instructions to answer only from provided context. On fallback, routes to the updater.
- **Updater layer (updater.py):** Human-in-the-loop component for unknown queries. Collects new error code details via CLI, checks for duplicates, appends to the CSV, and fully rebuilds the vector index from scratch.

## Data Flow

```
User Query
    │
    ▼
generator.generate()
    │
    ├── retriever.retrieve()
    │       ├── Embed query (all-MiniLM-L6-v2)
    │       ├── Query ChromaDB (top-3, cosine)
    │       └── Return results + fallback_needed flag
    │
    ├── [distance <= 0.4] → Build grounded prompt → gpt-4o-mini → Answer
    │
    └── [distance > 0.4] → updater.run_updater()
                                ├── Collect new error via CLI
                                ├── Append to CSV
                                └── Full re-index (delete + rebuild ChromaDB)
```

## Notable Design Decisions

- **Local embeddings, cloud LLM:** Embedding computation runs entirely locally using sentence-transformers (fast, free, no API calls). OpenAI is called only for the final generation step, minimizing latency and cost.
- **Fallback threshold (0.4):** A custom cosine distance cutoff that determines when to admit the system does not have a good answer rather than generating a low-confidence response. Prevents hallucination at the retrieval gate rather than relying solely on the LLM.
- **Paragraph-level chunking:** The equipment manual is split on blank line boundaries rather than fixed-size windows, preserving semantic coherence of each chunk.
- **Full rebuild on update:** When new data is added, the collection is deleted and rebuilt from scratch rather than incrementally upserted, ensuring index consistency.

## Technology Stack

Python, ChromaDB (HNSW, cosine similarity), Sentence-Transformers (all-MiniLM-L6-v2, 384-dim), OpenAI (gpt-4o-mini), Pandas, FastAPI (planned REST layer)

## Data Sources

- **error_codes.csv:** 15 structured MES error codes (ERR-001 to ERR-015) with descriptions, assembly lines, stations, and multi-step resolution procedures.
- **equipment_manuals.txt:** Synthetic plant operations manual covering assembly lines A/B/C, 8 stations, shift schedules, escalation procedures, quarantine zones, and safety protocols.

## Outcomes

- Fully functional CLI-based RAG pipeline from ingestion through retrieval to grounded generation.
- Fallback threshold correctly identifies out-of-distribution queries before they reach the LLM.
- Human-in-the-loop updater extends the knowledge base at runtime and rebuilds the vector index automatically.
- Demonstrates end-to-end understanding of the RAG architecture: chunking strategy, embedding model selection, vector store configuration, retrieval confidence gating, and grounded generation.
