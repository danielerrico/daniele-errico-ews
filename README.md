# Banking Crisis Early Warning System (1970-2017)

## Project Overview
This project performs a quantitative analysis of global financial stability using the **Systemic Banking Crises Database** (Laeven & Valencia, IMF). The objective is to examine the frequency, fiscal costs, and output losses associated with banking crises over the last five decades, with a specific focus on the 2008 Global Financial Crisis.

This repository demonstrates the application of data analytics techniques to unstructured financial datasets, bridging the gap between economic theory and empirical evidence.

## Data Source
The analysis utilizes the **Laeven and Valencia (2018)** dataset, which covers:
* **Crisis Dates:** Banking, currency, and sovereign debt crises.
* **Fiscal Costs:** Direct fiscal outlays relative to GDP.
* **Output Losses:** Cumulative loss in output relative to trend.
* **Policy Responses:** Liquidity support, recapitalizations, and guarantees.

**Source:** [Laeven, L., & Valencia, F. (2018). Systemic Banking Crises Database II. IMF Economic Review.](https://www.imf.org/en/Publications/WP/Issues/2018/09/14/Systemic-Banking-Crises-Revisited-46232)

## Methodology
The analysis was conducted using **Python** in a Jupyter Notebook environment. Key steps included:

1.  **Data Cleaning & Preprocessing:**
    * Handling missing values and inconsistencies in the raw dataset.
    * Structuring the data to isolate relevant economic indicators (Fiscal Costs, Output Loss).
2.  **Exploratory Data Analysis (EDA):**
    * Analyzing the distribution of crises across different income groups and regions.
    * Calculating descriptive statistics for fiscal interventions.
3.  **Visualization:**
    * Generating time-series plots to visualize crisis frequency peaks (e.g., 2008).
    * Creating comparative charts to analyze the severity of the 2008 crisis versus historical averages.

## Technologies Used
* **Python 3**
* **Pandas:** For data manipulation and aggregation.
* **Matplotlib / Seaborn:** For data visualization.
* **NumPy:** For numerical operations.

## Key Findings
* The analysis highlights the cyclical nature of banking crises, with significant peaks corresponding to major global economic downturns.
* Fiscal costs associated with the 2008 crisis were significantly higher in advanced economies compared to emerging markets, despite similar output losses.

## Usage
To reproduce the analysis:
1.  Clone the repository.
2.  Ensure `laeven-valencia.xlsx` is in the root directory.
3.  Run the `final.ipynb` Jupyter Notebook.
