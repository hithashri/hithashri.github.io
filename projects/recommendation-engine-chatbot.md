---
title: Real-Time Manufacturing Breakdown Recommendation System
permalink: /projects/recommendation-engine-chatbot/
---

<a class="back-link" href="/projects.html">← Projects</a>

# Real-Time Manufacturing Breakdown Recommendation System

## Executive Overview

Built a GPT-4o powered RAG chatbot that pulls system-generated error codes directly from the Manufacturing Execution System and delivers evidence-backed breakdown resolution guidance to technicians in real time, with no manual input required.

## Business Context

In a high-throughput production environment, downtime from equipment failures has direct impact on output and delivery timelines. Resolution knowledge existed across Excel logs, PDFs, and internal documentation, but retrieval was manual and inconsistent across shifts.

## Problem Statement

How can technicians receive fast, trustworthy resolution guidance for live breakdowns without manually searching fragmented records?

## Solution Design

- Consolidated structured and unstructured maintenance data into a unified retrieval-ready knowledge base.
- Implemented similarity-based retrieval to map live error signals to historically successful fixes.
- Integrated GPT-based response generation constrained to verified internal context.
- Added a feedback loop so technician-confirmed fixes could improve future ranking and response quality.

## System Design and Architecture

- **Ingestion layer:** Excel/PDF parsers for historical incident and resolution records.
- **Retrieval layer:** Similarity matching between incoming error events and known resolution clusters.
- **Reasoning layer:** GPT response composition using retrieved evidence and safety constraints.
- **Feedback layer:** Capture of accepted/rejected recommendations for iterative improvement.

Add your draw.io architecture diagram here later: `assets/diagrams/recommendation-system-architecture.png`.

## Technology Stack

Python, Azure OpenAI (GPT-4o), FastAPI, NLP pipelines, document parsing, similarity search

## Outcomes

- **96% accuracy** on known failure cases with evidence-backed recommendations.
- **100% safe fallback rate** for unseen error types, preventing incorrect guidance.
- Automated error code ingestion from MES with zero manual input.
- Reduced production downtime on the oxygen sensor line.
- Established a continuously improving, retrieval-backed support workflow.

## Confidentiality Note

Specific internal datasets, system identifiers, and implementation details are intentionally abstracted.
