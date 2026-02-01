# Systemic Banking Crises Analysis (1970-2017)

## Project Overview
This project performs a quantitative analysis of global financial stability using the **Systemic Banking Crises Database** (Laeven & Valencia, IMF). The objective is to examine the frequency, fiscal costs, and output losses associated with banking crises over the last five decades, with a specific comparative focus on the impact of the **2008 Global Financial Crisis** on Advanced Economies vs. Emerging Markets.

This repository demonstrates the application of data analytics techniques to unstructured financial datasets, bridging the gap between economic theory and empirical evidence.

## Data Source
The analysis utilizes the **Laeven and Valencia (2018)** dataset, focusing on:
* **Crisis Dates:** Banking, currency, and sovereign debt crises (filtered from 1970 onwards).
* **Fiscal Costs:** Direct fiscal outlays relative to GDP.
* **Output Losses:** Cumulative loss in output relative to trend.
* **Income Groups:** Classification of countries into Advanced Economies and Emerging Markets.

**Source:** [Laeven, L., & Valencia, F. (2018). Systemic Banking Crises Database II. IMF Economic Review.](https://www.imf.org/en/Publications/WP/Issues/2018/09/14/Systemic-Banking-Crises-Revisited-46232)

## Methodology
The analysis was conducted using **Python** in a Jupyter Notebook environment. Key analytical steps included:

1.  **Data Preprocessing:**
    * Loading the dataset and handling missing values (NaN) to ensure statistical accuracy.
    * Filtering data to focus on modern financial history (post-1970).
2.  **Exploratory Data Analysis (EDA):**
    * Calculating the frequency of crises per year to identify cyclical peaks.
    * Grouping data by "Income Group" to compare economic resilience.
3.  **Comparative Analysis (The 2008 Crisis):**
    * Isolating the 2008-2009 period to compare **Fiscal Costs** and **Output Losses**.
    * *Finding:* The code highlights that Advanced Economies faced significantly higher fiscal costs compared to Emerging Markets during this specific period.
4.  **Visualization:**
    * Used **Matplotlib** and **Seaborn** to generate bar charts and time-series plots for intuitive data communication.

## Technologies Used
* **Python 3**
* **Pandas:** For data manipulation, filtering, and aggregation.
* **Matplotlib / Seaborn:** For data visualization.
* **NumPy:** For numerical operations.

## Usage
To reproduce the analysis:
1.  Clone the repository.
2.  Ensure `laeven-valencia.xlsx` is in the root directory.
3.  Run the `final.ipynb` Jupyter Notebook.
