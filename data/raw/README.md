# Raw Data

## Overview

This folder contains the original, unmodified datasets used in the **Predicting the Severity of AI and LLM Vulnerabilities** project.

Raw data is preserved to ensure reproducibility and traceability throughout data cleaning, preprocessing, and machine learning experiments.

## Dataset Information

**Dataset:** AI Sec Watch Dataset v4.0  
**Release:** October 2026  
**Source:** [Zenodo – AI Sec Watch Dataset](https://zenodo.org/records/23282466)  
**License:** CC BY 4.0  
**Institution:** Texas State University

### Dataset Summary

- **8,260** AI security records with 48 columns, aggregated from 75 public sources, including NIST NVD, GitHub Advisory Database, and vendor advisories.
- **2,876** vulnerabilities affecting AI software, including LangChain, vLLM, MLflow, n8n, Flowise, TensorFlow, agent frameworks, and model APIs.
- **993 vulnerabilities (35%)** lack an official CVSS severity score.

### Available Features

The dataset includes:

- Vulnerability descriptions and CVSS scores
- Severity classifications (Low, Medium, High, Critical)
- Weakness types and affected software packages
- Attack types, including prompt injection, supply chain attacks, jailbreaks, data extraction, and model poisoning
- Targeted AI components, such as agents, plugins, RAG systems, and APIs
- Vendor and advisory information

## Research Relevance

Many AI vulnerabilities lack official severity ratings, creating challenges for security teams prioritizing remediation.

This dataset supports research into predicting vulnerability severity using machine learning, particularly:

- **Classification:** Predict severity levels from vulnerability descriptions and relevant metadata.
- **Regression:** Explore predicting numerical CVSS scores.
- **Clustering:** Identify patterns across attack types and targeted AI components.
- **Model Comparison:** Evaluate different machine learning approaches, including performance on newer vulnerabilities.

The project's primary objective is **severity classification**, with clustering as a supporting analysis.

## Data Handling

- **Raw data integrity:** Original files must remain unchanged.
- **Preprocessing:** Perform cleaning and transformations on copies of the raw data.
- **Processed data:** Store cleaned datasets in `data/processed/`.
- **Data leakage prevention:** Exclude CVSS scores, existing severity labels, and other fields that directly reveal the target severity from model inputs.
- **Reproducibility:** Document all cleaning and preprocessing steps.

## Citation

AI Sec Watch Dataset v4.0 (October 2026). Available from [Zenodo](https://zenodo.org/records/23282466).

Licensed under Creative Commons Attribution 4.0 International (CC BY 4.0).
