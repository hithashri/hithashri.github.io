---
title: "Why Retrieval Quality Matters More Than Model Size in RAG"
date: 2026-04-22
---

I have been reading a lot about RAG pipelines lately, and one thing that keeps coming up is how much the retrieval step matters. People focus on which LLM to use, but if the retriever pulls in irrelevant or noisy context, even the best model will produce unreliable output.

What surprised me is how much of a difference BM25 still makes as a baseline. Semantic search with embeddings is powerful, but combining it with keyword-based ranking often gives better results than either alone.

This connects directly to the validation framework I am building at UCI. If the retrieved evidence is poor, the grounding check fails regardless of the model. Retrieval quality is the foundation.
