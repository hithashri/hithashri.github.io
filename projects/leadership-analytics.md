---
title: Daily Leadership Review Chatbot
permalink: /projects/leadership-analytics/
---

<a class="back-link" href="/projects.html">← Projects</a>

# Daily Leadership Review Chatbot

## Executive Overview

Developed a conversational analytics assistant for leadership that delivers live manufacturing KPI insights from enterprise databases through natural language interaction.

## Business Context

Leadership teams relied heavily on static dashboards for operational monitoring. This approach introduced friction, reduced agility for ad hoc questions, and required broad licensing.

## Problem Statement

How do we provide faster, easier, and more cost-effective access to operational metrics for leadership decision-making?

## Solution Design

- Connected to live Manufacturing Execution System data sources.
- Encoded KPI definitions, formulas, and context for consistent metric interpretation.
- Built secure backend APIs to fetch and assemble response-ready data.
- Enabled natural-language querying through an LLM-powered interface.

## System Design and Architecture

- **Data layer:** Live Oracle MES data integration.
- **Business logic layer:** KPI definitions, aggregation rules, and context injection.
- **API layer:** FastAPI endpoints for controlled query orchestration.
- **Interaction layer:** LLM-based conversational interface for leadership users.

Add your draw.io architecture diagram here later: `assets/diagrams/leadership-review-chatbot-architecture.png`.

## Technology Stack

Azure OpenAI (GPT-4o), Oracle SQL, FastAPI, TypeScript, REST APIs

## Outcomes

- **Eliminated the need for 150+ Power BI licenses** by replacing static dashboards with conversational access.
- Delivered real-time KPI insights to plant leadership through natural language queries.
- Reduced decision latency by connecting directly to live Oracle MES data via REST API.
