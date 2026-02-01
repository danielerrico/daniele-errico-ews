# Banking Crisis Early Warning System (EWS)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=flat&logo=python)
![Status](https://img.shields.io/badge/Status-Academic%20Research-orange)
![License](https://img.shields.io/badge/License-MIT-green)

##  Project Abstract
This research project implements a quantitative **Early Warning System (EWS)** designed to predict systemic banking crises 12 months in advance. By analyzing over 40 years of macroeconomic data across **37 OECD nations and China**, the model identifies the buildup of financial vulnerabilities (such as overheating credit markets) before they materialize into full-blown crises.

The framework bridges **economic theory** with **machine learning**, utilizing a strictly historical simulation (Walk-Forward Validation) to prevent look-ahead bias.

##  Data Sources
The dataset is constructed by merging two primary sources via an automated ETL pipeline:
1.  **Target Variable ($Y$):** Systemic Banking Crises Database (Laeven & Valencia, IMF).
    * *Covers:* Banking crises, currency crises, and sovereign debt defaults (1970–2017).
2.  **Features ($X$):** World Development Indicators (World Bank).
    * *Indicators:* Credit-to-GDP gaps, Inflation, Real Interest Rates, M2 Money Supply, and Terms of Trade.

##  Methodology & Rigor
Unlike standard predictive models, this project addresses the specific challenges of financial time-series analysis:

### 1. Walk-Forward Validation (Rolling Origin)
To simulate real-world forecasting conditions, standard Cross-Validation (K-Fold) was rejected. Instead, the model uses an expanding window approach:
* *Train:* Years $[T_{start}, T_{current}]$
* *Test:* Year $[T_{current} + 1]$
* *Result:* This ensures the model never "sees" the future, strictly validating its ability to predict the 2008 Global Financial Crisis using only pre-2007 data.

### 2. Signal Processing
Raw macroeconomic data is non-stationary. The pipeline transforms features using:
* **Z-Score Standardization:** To normalize volatility across different economies.
* **Hodrick-Prescott (HP) Filter:** To isolate the cyclical component of Credit-to-GDP (the "Credit Gap"), a key predictor of instability.

### 3. Optimization for "Recall"
In financial stability, a False Negative (missing a crisis) is significantly more costly than a False Positive (a false alarm). The model threshold is optimized to maximize **Recall**, ensuring policymakers are alerted to potential risks even at the cost of higher sensitivity.

##  Key Findings & Interpretation
* **The 2008 Asymmetry:** The analysis reveals that while Advanced Economies faced higher **Fiscal Costs** (bailouts/recapitalizations) during 2008, Emerging Markets suffered proportionally higher **Output Losses** relative to their trend.
* **Leading Indicators:** The Feature Importance analysis confirms that deviations in the **Credit-to-GDP gap** and rapid spikes in **Real Interest Rates** are the strongest predictors of impending banking distress.

##  Technologies
* **Core:** Python 3, NumPy.
* **Data Engineering:** Pandas, Wbdata (World Bank API), Country_converter.
* **Analysis:** Scikit-Learn (Logistic Regression/Random Forest), Statsmodels.
* **Visualization:** Matplotlib, Seaborn.

##  Usage
To replicate the analysis:

1.  Clone the repository:
    ```bash
    git clone [https://github.com/YOUR_USERNAME/banking-crisis-ews.git](https://github.com/YOUR_USERNAME/banking-crisis-ews.git)
    ```
2.  Install dependencies:
    ```bash
    pip install pandas numpy scikit-learn matplotlib wbdata country_converter
    ```
3.  Run the Jupyter Notebook:
    ```bash
    jupyter notebook final.ipynb
    ```

---
*Author: Daniele Errico*
