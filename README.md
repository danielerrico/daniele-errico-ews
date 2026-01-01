# 🏦 Banking Crisis Early Warning System: Target Generation Module

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Engineering-green)
![Stage](https://img.shields.io/badge/Stage-Target%20Definition-orange)

## 🔭 Project Overview & Vision
This project aims to apply **Machine Learning** to the field of Macroeconomics to build an **Early Warning System (EWS)** for systemic banking crises.

The ultimate goal is to verify whether algorithmic models can identify the build-up of financial vulnerabilities (e.g., credit bubbles, overheating economies) **years before** a crisis actually occurs. To achieve this, the project follows a Supervised Learning approach:

1.  **Define the "Ground Truth" (Target Variable $Y$):** Accurately identify when and where crises happened historically.
2.  **Gather Economic Data (Features $X$):** Collect historical macroeconomic indicators (GDP, Inflation, Credit).
3.  **Train Models:** Use algorithms (Random Forest, XGBoost) to predict $Y$ using $X_{t-1}$.

**⚠️ Current Status:** This repository currently focuses on **Step 1: The Automated Generation of the Target Variable.**

---

## 🏛️ The Data Source: Laeven & Valencia

To train an AI, we first need a reliable label of "Crisis" vs "Non-Crisis."
We utilize the **Systemic Banking Crises Database**, created by Luc Laeven and Fabian Valencia (International Monetary Fund).

* **Why this dataset?** It is considered the academic "Gold Standard" for dating financial crises.
* **Coverage:** It tracks banking, currency, and sovereign debt crises globally from 1970 to 2017.
* **Format:** The raw data is hosted on the IMF website as an Excel file nested within a ZIP archive.

---

## ⚙️ Implemented Pipeline (ETL)

We have built a fully automated Python pipeline to handle the **Data Ingestion** and **Cleaning** of this target dataset. The script performs the following operations without manual intervention:

### 1. Automated Ingestion (Extract)
Instead of relying on local files, the script connects directly to the IMF servers.
* **Dynamic Fetching:** Uses `requests` to download the latest available `.zip` archive.
* **In-Memory Extraction:** Utilizes `zipfile` and `io` to locate and extract the specific Excel workbook (`.xlsx`) containing the crisis dates, bypassing the need to save temporary files to disk.

### 2. Data Cleaning & Parsing (Transform)
The raw IMF data is designed for human reading (containing footnotes, annotations, and mixed formats). The pipeline transforms this into machine-readable data:
* **Noise Reduction:** Removes metadata, empty rows, and footnotes (filtering out rows where country names are actually descriptive text).
* **Regex Date Parsing:** Implements Regular Expressions to handle complex date formats (e.g., converting *"2007 (ongoing)"* or *"Sept 2008"* into clean integers like `2007` and `2008`).

### 3. Geographical Standardization
To ensure this data can later be merged with World Bank economic indicators, precise geographical matching is required:
* **ISO3 Conversion:** The pipeline uses the `country_converter` library to translate raw country names (e.g., *"Korea, Rep."*, *"United States"*) into standard **ISO3 codes** (`KOR`, `USA`).
* **Entity Validation:** Filters out regional aggregates or unrecognized entities, ensuring only valid sovereign states remain.

---

## 📂 Current Output

The pipeline outputs a clean, standardized DataFrame representing the **Target Variable**, ready for future merging:

| iso3 | start_year | end_year |
|------|------------|----------|
| USA  | 2007       | 2011     |
| GBR  | 2007       | 2010     |
| ESP  | 2008       | 2012     |

---

## 🛣️ Roadmap & Next Steps

We have successfully defined the **Target ($Y$)**. The next development phases involve:

- [x] **Target Definition:** Auto-download and clean Laeven-Valencia data.
- [ ] **Feature Engineering:** Download Macroeconomic indicators (GDP, Credit, Rates) from the World Bank.
- [ ] **Data Merging:** Align Crisis dates with Economic data.
- [ ] **Modeling:** Train Machine Learning models to predict the onset of these crises.

---

## 💻 Requirements

To run the ingestion script:

```bash
pip install pandas country_converter requests openpyxl
