# FMR OCR-to-Analytics Data Pipeline

## Executive Overview

Designed and implemented an automated data pipeline that converts machine-generated PDF reports into structured datasets for near real-time quality analytics.

## Business Context

Quality teams received critical manufacturing reports in non-readable PDF formats, requiring manual extraction and slowing response to non-compliant part detection.

## Problem Statement

How can machine-generated PDF data be transformed into accurate, structured, and analytics-ready outputs with minimal manual work?

## Solution Design

- Built OCR and parsing workflows to extract tabular data from generated PDFs.
- Standardized extracted records into structured Excel/dataframe outputs.
- Implemented OK/NOK classification logic for rapid quality filtering.
- Integrated processed outputs with Power BI dashboards for continuous monitoring.

## System Design and Architecture

- **Input layer:** Shared storage source for machine-generated PDFs.
- **Extraction layer:** OCR + parsing for table reconstruction.
- **Transformation layer:** Data cleaning, normalization, and compliance tagging.
- **Consumption layer:** Excel outputs and BI dashboards for operations teams.

Add your draw.io dataflow diagram here later: `assets/diagrams/fmr-data-pipeline-architecture.png`.

## Technology Stack

Python, Tesseract OCR, PyMuPDF, Pandas, Excel automation, Power BI

## Outcomes

- Eliminated manual extraction effort from repetitive PDF reports.
- Improved response speed for defect identification and quarantine workflows.
- Enabled more reliable near real-time visibility into quality trends.
