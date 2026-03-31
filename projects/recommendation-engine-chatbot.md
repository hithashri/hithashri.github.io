# Real-Time Manufacturing Breakdown Recommendation System

## Executive Overview

Built an internal GPT-powered manufacturing assistant to provide reliable, real-time breakdown recommendations from historical resolution data, reducing manual troubleshooting effort on the shop floor.

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

- Faster root-cause guidance for common failures.
- Improved consistency of operator response across teams.
- Established a continuously improving, retrieval-backed support workflow.

## Confidentiality Note

Specific internal datasets, system identifiers, and implementation details are intentionally abstracted.
