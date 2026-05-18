---
title: Validation of LLMs Framework
permalink: /projects/llm-validation-framework/
---

<a class="back-link" href="/projects.html">← Projects</a>

# Validation of LLMs Framework

<div class="project-links">
  <a href="https://tyeoh9.github.io/llm-validation-framework/" class="btn btn-primary" target="_blank" rel="noopener">Documentation ↗</a>
  <a href="https://pypi.org/project/validate-llm/" class="btn btn-outline" target="_blank" rel="noopener">PyPI Package ↗</a>
</div>

## Executive Overview

Led a 4-person team to architect and publish `validate-llm`, an open-source Python package on PyPI that delivers five composable guardrail agents — toxicity, privacy, accuracy, relevancy, and bias — wrapping any LLM pipeline with structured PASS/FAIL verdicts and calibrated 0–1 scoring. Supports multiple providers via LiteLLM.

<div class="metrics-row">
  <span class="metric-chip">96% toxicity detection</span>
  <span class="metric-chip">85% accuracy on benchmarks</span>
  <span class="metric-chip">5 guardrail agents</span>
  <span class="metric-chip">Zero external API calls for safety</span>
</div>

## Business Context

As LLM systems move into production, organizations need reliable, composable safeguards before responses reach users. Validation pipelines must detect harmful, biased, or ungrounded outputs early and consistently — without forcing teams to build custom detection logic from scratch.

## Problem Statement

How can we design an automated, extensible framework to evaluate LLM responses across safety, privacy, factual grounding, relevancy, and bias — while remaining provider-agnostic and production-ready?

## Solution Design

- **Composable guardrail architecture:** Five independent agents (toxicity, privacy, accuracy, relevancy, bias) that plug into any LLM pipeline as input or output guardrails, each returning structured verdicts and calibrated scores.
- **3-layer toxicity detection:** Combined rule-based profanity filtering, Detoxify ML scoring, and SentenceTransformer (all-MiniLM-L6-v2) semantic similarity classification across policy categories (hate speech, violence, extremism, self-harm) — achieving **96% detection accuracy** with fully local inference and zero external API calls.
- **Plug-and-play RAG interface:** Developers can integrate their own vector store retriever for domain-specific factual grounding. The default accuracy agent uses LLM-as-a-judge via DeepEval GEval with BM25-ranked web retrieval as the evidence source, reaching **85% accuracy** on benchmarks.
- **Privacy agent:** Regex-based PII and secrets scanning — detects SSNs, credit cards (Luhn-validated), API keys, and system prompt leakage, all running locally.
- **Multi-provider support:** LiteLLM integration enabling seamless switching between Anthropic, OpenAI, and other LLM providers.

## System Design and Architecture

- **Orchestration layer:** Sequential fail-fast agent pipeline with early termination on critical failures.
- **Toxicity layer:** Rule-based filters → Detoxify model scoring → semantic policy mapping via SentenceTransformers.
- **Privacy layer:** Regex-based PII detection with Luhn validation for credit cards and pattern matching for secrets.
- **Grounding layer:** Configurable RAG retriever interface, BM25 ranking, and LLM-as-a-judge evaluation.
- **Relevancy & Bias layers:** LLM-as-a-judge detection of off-topic responses, stereotypes, discriminatory language, and unfair generalisations.
- **Output layer:** Structured validation report with per-agent verdicts, confidence scores, and aggregate status.
- **Demo stack:** FastAPI backend with SSE streaming + web UI for interactive testing.

<!-- Add your draw.io validation architecture diagram here later: assets/diagrams/llm-validation-framework-architecture.png -->

## Technology Stack

Python, LiteLLM, DeepEval (GEval), Detoxify, SentenceTransformers (all-MiniLM-L6-v2), BM25 retrieval, FastAPI, SSE streaming

## Outcomes

- Published to [PyPI](https://pypi.org/project/validate-llm/){:target="_blank"} as a pip-installable package with full [documentation site](https://tyeoh9.github.io/llm-validation-framework/){:target="_blank"}.
- **96%** toxicity detection accuracy with fully local, zero-API-call inference.
- **85%** factual accuracy on benchmarks using LLM-as-a-judge with BM25 evidence retrieval.
- Shipped a full-stack demo (FastAPI + SSE streaming + web UI) for interactive pipeline testing.
- Designed for production extensibility — teams can plug in custom retrievers, swap providers, and configure per-agent thresholds.

## Quick Start

```
pip install validate-llm
```

```python
from llm_validation_framework import (
    ValidationFramework, LLMProvider, Pipe,
    ToxicityAgent, AccuracyAgent,
)
from llm_validation_framework.config_loader import load_api_key

api_key = load_api_key(provider="ANTHROPIC")
llm = LLMProvider(provider="anthropic", model="claude-haiku-4-5-20251001", key=api_key)

input_guardrail  = Pipe(steps=[ToxicityAgent()], verbose=False)
output_guardrail = Pipe(steps=[ToxicityAgent(), AccuracyAgent()], verbose=False)

vf = ValidationFramework(llm=llm, input_guardrail=input_guardrail, output_guardrail=output_guardrail)
result = vf.validate("What is the Pacific Ocean?")

print(result["status"])  # "PASS" or "FAIL"
print(result["score"])   # 0.0 – 1.0
```
