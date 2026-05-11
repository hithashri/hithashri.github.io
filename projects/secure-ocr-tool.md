---
title: Secure On-Prem OCR Tool
permalink: /projects/secure-ocr-tool/
---

<a class="back-link" href="/projects.html">← Projects</a>

# Secure On-Prem OCR Tool

## Executive Overview

Built and deployed the first Python-based web application on the Bosch plant network -- an OCR tool for secure digitization of sensitive HR and legacy documents, hosted entirely within corporate firewall restrictions.

## Business Context

Large volumes of scanned records were non-searchable, slowing retrieval and compliance workflows. External OCR services were not acceptable due to confidentiality constraints.

## Problem Statement

How can we digitize legacy scanned documents at scale without exposing data beyond internal enterprise networks?

## Solution Design

- Developed a Flask-based OCR web interface for internal users.
- Implemented document processing and text extraction workflows for scanned records.
- Hosted and served the app on-prem using enterprise-compatible service hosting.
- Ensured no external data transfer outside internal network boundaries.

## System Design and Architecture

- **Access layer:** Internal-only web interface for document upload and extraction.
- **Processing layer:** OCR engine and post-processing normalization.
- **Deployment layer:** On-prem Windows service setup (Waitress/NSSM).
- **Security layer:** Network-bound operation with no third-party data exposure.

Add your draw.io deployment architecture here later: `assets/diagrams/secure-ocr-tool-architecture.png`.

## Technology Stack

Python, Flask, OCR stack, Waitress, NSSM, internal server deployment

## Outcomes

- **First Python-based web application** ever deployed on the Bosch plant network.
- Independently designed the hosting solution within corporate firewall restrictions using Waitress and NSSM.
- Enabled secure digitization of sensitive HR documents with zero external data exposure.
