# AAI-501-TEAM2
Team 2 Final Project - AAI-501
# Predicting the Severity of AI and LLM Vulnerabilities

**University of San Diego | MS in Applied Artificial Intelligence**  
**Course:** AAI-501 – Introduction to Artificial Intelligence  
**Team 2:** Olena McMurtrey, Kate Cher, Aren Sinaei

## Project Overview

This project explores how machine learning can predict the severity of security vulnerabilities in AI and Large Language Model (LLM) systems based on vulnerability descriptions and related characteristics.

The goal is to classify vulnerabilities into four severity levels:

- **Low**
- **Medium**
- **High**
- **Critical**

By predicting severity before an official rating is available, the system aims to support security teams in prioritizing vulnerability reviews and remediation.

## Dataset

The project uses the **AI Sec Watch Dataset (Version 4.0)**, a public collection of AI and LLM security vulnerability records.

The dataset includes vulnerability descriptions, severity ratings, weakness types, attack types, and affected components.

**Source:** [AI Sec Watch Dataset – Zenodo](https://doi.org/10.5281/zenodo.19519469)

## Methodology

The project follows a supervised machine learning approach, supported by exploratory analysis and clustering.

### Data Preparation
- Examine data quality and missing values.
- Prepare text descriptions and categorical features.
- Address class imbalance across severity levels.
- Exclude CVSS scores and other severity-revealing features to prevent data leakage.
- Apply a time-based training and testing split.

### Machine Learning Models
- **Logistic Regression:** Baseline classification model.
- **Random Forest:** Comparative classification model.
- **Clustering:** Supporting unsupervised analysis to explore vulnerability patterns.
- **Neural Network (Optional):** Additional model if time permits.

### Model Evaluation
Models will be evaluated using:

- Accuracy
- Precision
- Recall
- F1-score, with emphasis on **Macro F1**
- ROC curves
- Recall for critical vulnerabilities

Special attention will be given to minimizing missed critical vulnerabilities.

## Expected Outcomes

The system is intended to:

1. Predict vulnerability severity from descriptions and relevant features.
2. Generate probability estimates for each severity class.
3. Compare the performance of different classification models.
4. Identify features and patterns associated with vulnerability severity.
5. Explore how machine learning can support security vulnerability prioritization.

## Technologies

- Python
- pandas and NumPy
- scikit-learn
- Jupyter Notebooks
- Machine Learning and Natural Language Processing (NLP)

## Project Status

**In Development** — Academic research project.

## References

- Luu, T. J. (2026). *AI Sec Watch Dataset: AI/LLM Security Threat Intelligence (Version 4.0).* [Zenodo](https://doi.org/10.5281/zenodo.19519469)
- Pedregosa et al. (2011). *Scikit-learn: Machine Learning in Python.* [Journal of Machine Learning Research](https://jmlr.org/papers/v12/pedregosa11a.html)
- Poole & Mackworth (2023). *Artificial Intelligence: Foundations of Computational Agents.* [Textbook](https://artint.info/3e/html/ArtInt3e.html)

## Disclaimer

This project is developed for academic and research purposes. Predicted severity ratings are experimental and should not replace official security assessments or professional vulnerability analysis.
