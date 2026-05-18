---
title: Real-Time Manufacturing Breakdown Recommendation System
permalink: /projects/recommendation-engine-chatbot/
---

<a class="back-link" href="/projects.html">← Projects</a>

# Real-Time Manufacturing Breakdown Recommendation System

## Executive Overview

Built a GPT-4o powered breakdown resolution assistant for a high-throughput oxygen sensor production line at Bosch, integrating directly with the Manufacturing Execution System to deliver grounded, evidence-backed guidance to technicians in real time with zero manual input required. Deployed to production on the factory floor.

## Business Context

In a high-throughput production environment, equipment downtime has direct impact on output and delivery timelines. Resolution knowledge existed across Excel logs, PDFs, and internal documentation, but retrieval was manual, inconsistent across shifts, and dependent on individual technician experience.

## Problem Statement

How can technicians receive fast, trustworthy resolution guidance for live breakdowns without manually searching fragmented records, and how can the system handle error types it has never seen before without producing incorrect guidance?

## Solution Design

- Consolidated structured error code records and unstructured maintenance documentation into a unified, retrieval-ready knowledge base.
- Built a retrieval pipeline that maps live MES error signals to historically verified resolution steps from the internal knowledge base.
- Integrated GPT-4o response generation constrained strictly to retrieved internal context, preventing hallucination outside the knowledge base.
- Implemented a safe fallback mechanism that gracefully handles unknown error types without generating unverified guidance.
- Deployed the system directly within the plant network, integrated with live MES error code ingestion.

## System Design and Architecture

- **Ingestion layer:** Structured error code records and unstructured maintenance documentation parsed and loaded into the knowledge base.
- **Retrieval layer:** Incoming MES error signals mapped to verified resolution records from the internal knowledge base.
- **Reasoning layer:** GPT-4o response generation using Azure OpenAI, constrained to retrieved context via system prompt with strict grounding instructions.
- **Fallback layer:** Confidence-gated fallback logic that detects low-confidence retrievals and returns a safe, explicit non-answer rather than a hallucinated response.
- **Deployment layer:** FastAPI backend, deployed on-premise within the Bosch plant network.

## Technology Stack

Python, Azure OpenAI (GPT-4o), FastAPI, structured and unstructured document parsing, on-premise deployment

## Outcomes

- **96% accuracy** on known failure cases with evidence-backed, grounded recommendations.
- **100% safe fallback rate** for unseen error types, preventing incorrect guidance from reaching the factory floor.
- Zero manual input required from technicians; error codes ingested directly from MES.
- Reduced production downtime on the oxygen sensor line.
- Successfully deployed as a production system within the Bosch plant network.

## Note

This was a production system built on proprietary Bosch infrastructure. Specific datasets, internal system identifiers, and implementation details are intentionally abstracted. A standalone RAG prototype implementing the core vector search architecture is [documented separately](/projects/mes-rag-chatbot/).
