# Raw Data

This folder contains the original datasets used in this project.

- **Purpose:** Store source data before cleaning, preprocessing, or transformation.
- **Data integrity:** Raw files should remain unchanged to ensure reproducibility.
- **Processing:** Cleaned and transformed datasets are stored separately in the `processed_data` folder.

All data cleaning and preprocessing should be performed on copies of the raw files.
Data: https://zenodo.org/records/23282466
Why it matters
993 of 2,876 AI vulnerabilities in the dataset (35%) have no official CVSS severity score yet. Security teams still have to decide what to patch first. We could build models that estimate severity from the description and metadata.

The data
• AI Sec Watch Dataset v4.0, Oct 2026, CC BY 4.0 (Zenodo, Texas State University)
• 8,260 AI security records, 48 columns, from 75 public sources including NIST NVD, GitHub Advisory and vendor advisories
• 2,876 vulnerabilities in AI software: LangChain, vLLM, MLflow, n8n, Flowise, TensorFlow, agent frameworks and model APIs
• Columns include CVSS score, severity, weakness type, affected package, attack type (prompt injection, supply chain, jailbreak, data extraction, model poisoning), AI component targeted (agent, plugin, RAG, API) and vendor

Potential areas to explore
• Regression: predict the CVSS score (0-10) on 1,883 scored records
• Classification: predict the severity level (low, medium, high, critical) on 2,444 records
• Clustering: group vulnerabilities by attack pattern and targeted AI component
• Experimental comparison: several models per task, plus a time test (train before 2026, test on 2026)
• Demo: score the 993 unscored vulnerabilities
