# 🏦 Systemic Banking Crises Data Pipeline

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Cleaning-green)
![Data Source](https://img.shields.io/badge/Source-IMF%20(Laeven%20%26%20Valencia)-blueviolet)

## Project Objective
The goal of this repository is to build a robust, **automated pipeline** to ingest and standardize historical data on Systemic Banking Crises.

This specific module focuses on the **Target Variable**: accurately identifying the Start and End years of banking crises worldwide, transforming "messy" Excel data into a clean, machine-readable format for downstream analysis.

---

## Data Source

The project relies on the "Gold Standard" for financial crisis dating:

* **Database:** Systemic Banking Crises Database.
* **Authors:** Luc Laeven & Fabian Valencia (IMF).
* **Content:** A comprehensive database of banking crises, currency crises, and sovereign debt crises from 1970 to 2017.
* **Original Format:** Excel file (`.xlsx`) contained within a ZIP archive hosted on the IMF website.

---

## The Pipeline

We have developed a "One-Click" Python script that handles the entire ETL (Extract, Transform, Load) process without manual intervention.

### 1. Automated Extraction
* **Direct Download:** The script uses the `requests` library to fetch the dataset directly from the IMF server (bypassing manual browser downloads).
* **Zip Handling:** It utilizes `zipfile` and `io` to extract the specific Excel workbook from memory, handling dynamic filenames automatically.

### 2. Data Cleaning & Parsing
The original dataset contains footnotes, non-standard text, and ongoing events. The pipeline performs:
* **Noise Removal:** Filters out empty rows, footnotes, and metadata descriptions.
* **Date Parsing:** Uses **Regular Expressions (Regex)** to extract clean years (4 digits) from mixed text fields (e.g., handling "1997-", "ongoing", or annotated dates).
* **Duration Logic:** Imputes missing "End Dates" (assuming single-year duration if not specified) to create a continuous timeline.

### 3. Geographical Standardization
* **ISO3 Conversion:** Utilizes the `country_converter` library to translate varied country names (e.g., "Korea, Rep.", "United States") into standard **ISO3 codes** (KOR, USA).
* **Validation:** Removes regional aggregates or unrecognized entities to ensure 100% geographical consistency.

---

## Output Structure

The processed dataset results in a clean table ready for merging with economic indicators.

| iso3 | start_year | end_year | Country Name (Raw) |
|------|------------|----------|--------------------|
| USA  | 2007       | 2011     | United States      |
| GBR  | 2007       | 2010     | United Kingdom     |
| ISL  | 2008       | 2011     | Iceland            |
| ITA  | 2008       | 2014     | Italy              |

---

## Roadmap

- [x] **Automation:** Script downloads and unzips data automatically.
- [x] **Standardization:** ISO3 codes and Clean Years implemented.
- [ ] **Data Enrichment:** Integrate Macroeconomic variables (GDP, Credit, etc.) to analyze causes.
- [ ] **Visualization:** Plot the frequency of crises over time.

---

##  Requirements

To run the pipeline, install the necessary dependencies:
