
# AAI 501 – Data Cleaning (Kate)

## Project Overview

This folder contains my cleaned dataset and preprocessing documentation for the **AAI 501 Final Project: Predicting the Severity of AI and LLM Vulnerabilities**.

The objective is to prepare reliable data for machine learning models that classify vulnerabilities as Low, Medium, High, or Critical.

## Data Cleaning Methodology

The original AI Sec Watch dataset contained **8,260 records and 48 columns**.

After preprocessing, the final dataset contains **2,444 records and 18 columns**.

Key preprocessing steps:

- Filtered records to retain eligible CVSS-based severity labels.
- Examined missing values and duplicate records.
- Corrected **10 inconsistent severity labels** using CVSS scores.
- Removed explicit severity ratings and potential target leakage from model text.
- Replaced **3,860 CVE/GHSA identifier occurrences**.
- Removed repetitive TensorFlow boilerplate from **386 records**.
- Performed additional text cleanup on **86 records**.
- Created a chronological **80/20 train/test split**.
- Performed final data quality and reproducibility checks.

## Final Dataset

- **Training set:** 1,955 records
- **Testing set:** 489 records
- **Target variable:** `severity`
- **Text feature:** `model_text`

Audit fields and potentially leaking variables must be excluded from model training.

## Project Files

- `AAI501_Kate_Cleaned_Dataset_FINAL.csv` – Final cleaned dataset.
- `AAI_501_Kate_Cleaning_FINAL.ipynb` – Data cleaning notebook.
- `AAI501_Kate_Data_Cleaning_Methodology_APA7_Revised.pdf` – Detailed APA 7 methodology report.

## Next Steps

The cleaned dataset will support severity classification using machine learning models, including **Random Forest**.

---

**University of San Diego**  
**AAI 501 – Introduction to Artificial Intelligence**
