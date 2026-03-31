# Real-Time Helmet Detection and Violation Logging System

## Executive Overview

Built a computer vision system to detect helmet non-compliance from CCTV footage and automatically log associated vehicle details for enforcement workflows.

## Business Context

Manual monitoring of traffic safety footage is resource-intensive and inconsistent. Automated detection can improve enforcement speed and coverage.

## Problem Statement

How can we detect non-helmet riders in real time and generate structured violation logs with minimal manual intervention?

## Solution Design

- Trained and deployed a YOLOv3-based detector for helmet compliance classification.
- Processed CCTV streams in real time using OpenCV.
- Logged non-compliance incidents with extracted vehicle number plate information.
- Automated reporting output into Excel for downstream review and action.

## System Design and Architecture

- **Input layer:** CCTV video stream ingestion.
- **Detection layer:** YOLOv3 inference for helmet/non-helmet identification.
- **Extraction layer:** Number plate capture and metadata structuring.
- **Reporting layer:** Automated tabular violation reports.

Add your draw.io system diagram here later: `assets/diagrams/helmet-detection-architecture.png`.

## Technology Stack

Python, YOLOv3, OpenCV, reporting automation

## Outcomes

- Reduced manual video monitoring effort.
- Improved consistency and traceability of safety violation records.
