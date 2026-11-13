# Project Proposal

## Predicting the Severity of AI and LLM Vulnerabilities

**Course:** AAI-501 – Introduction to Artificial Intelligence  
**University:** University of San Diego  
**Team 2:** Olena McMurtrey, Kate Cher, Aren Sinaei

## Overview

This folder contains the original project proposal outlining the research objectives, methodology, and expected outcomes of our AI vulnerability severity prediction project.

The project investigates whether machine learning can predict the severity of AI and Large Language Model (LLM) software vulnerabilities using their written descriptions and related metadata.

## Research Objective

Develop and evaluate machine learning models that classify AI software vulnerabilities into four severity levels:

- Low
- Medium
- High
- Critical

The goal is to support security teams in prioritizing vulnerabilities before official severity ratings become available.

## Proposed Methodology

**Dataset:** [AI Sec Watch Dataset v4.0](https://doi.org/10.5281/zenodo.19519469)

**Machine Learning Approaches:**
- **Logistic Regression:** Baseline classification model.
- **Random Forest:** Comparative classification model.
- **Clustering:** Supporting analysis to identify vulnerability patterns.
- **Neural Network:** Optional extension if time permits.

**Data Preparation:**
- Clean and preprocess vulnerability descriptions and metadata.
- Exclude CVSS scores and severity-revealing fields to prevent data leakage.
- Address class imbalance and potential label quality concerns.
- Use a time-based training and testing split.

**Evaluation Metrics:**
- Accuracy
- Precision and Recall
- Macro F1-score
- ROC curves
- Critical vulnerability recall

## Expected Outcomes

- Predict vulnerability severity from descriptions and relevant metadata.
- Estimate probabilities for each severity class.
- Compare classification model performance.
- Explore patterns in AI security vulnerabilities.
- Evaluate the potential of machine learning for vulnerability prioritization.

## Project Scope

The primary focus is **supervised severity classification**, supported by exploratory clustering. Deep learning is an optional extension.

The proposal defines the planned research approach; model performance and conclusions will be documented in the final report.

## Project Files

For datasets, notebooks, results, and final deliverables, refer to the repository's main `README.md`.
