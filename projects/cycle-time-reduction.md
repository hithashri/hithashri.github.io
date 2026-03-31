# Cycle Time Reduction via Predictive Modeling

## Executive Overview

Used statistical analysis and machine learning on calibration bench data to reduce unnecessary test operations while preserving quality standards.

## Business Context

The production calibration process used 20 test points per unit, creating a throughput bottleneck. Expanding test capacity required significant capital expenditure.

## Problem Statement

Can we remove redundant test steps using predictive modeling while maintaining acceptable quality and reliability?

## Solution Design

- Performed EDA to understand feature correlations, noise, and process stability.
- Trained and validated regression models to estimate later-stage measurements.
- Evaluated prediction confidence and quality tolerance thresholds with process engineers.
- Recommended selective elimination of low-value test points under controlled conditions.

## System Design and Architecture

- **Data layer:** Historical test-bench measurements and process metadata.
- **Modeling layer:** Regression pipeline for downstream test-point prediction.
- **Validation layer:** Quality threshold checks and error-bound governance.
- **Operations layer:** Decision criteria for retaining vs. skipping specific tests.

Add your draw.io pipeline or model flow here later: `assets/diagrams/cycle-time-model-architecture.png`.

## Technology Stack

Python, Pandas, NumPy, Scikit-learn, Support Vector Regression, visualization

## Outcomes

- Reduced cycle time by 9 seconds per unit.
- Improved productivity by 2.6%.
- Avoided approximately INR 40M in potential capacity expansion costs.
