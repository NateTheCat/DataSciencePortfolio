# Kia & Hyundai Theft Trend Analysis Across U.S. Cities

## Overview

This project analyzes trends in Kia and Hyundai vehicle thefts across multiple U.S. cities. It combines multiple datasets from police reports, city-level records, and VICE News to create a clean, unified dataset. The analysis focuses on monthly theft counts, proportions of Kia/Hyundai thefts compared to all vehicle thefts, and changes over time.

---

## Datasets

* **Car Thefts Map Dataset**

  * **Source:** Local police agencies
  * **Observations:** 556 entries
  * **Features:** City, year, latitude, longitude, theft counts (2019–2022), percent change

* **Kia and Hyundai Milwaukee Dataset**

  * **Source:** Local Milwaukee police reports
  * **Observations:** 48 entries
  * **Features:** Month, year, Kia/Hyundai thefts, other thefts, percent Kia/Hyundai, total thefts

* **Kia Hyundai Thefts Dataset**

  * **Source:** City-level theft data compiled from multiple sources
  * **Observations:** 552 entries
  * **Features:** Month, year, city, state, Kia/Hyundai thefts, other thefts, percent Kia/Hyundai, total thefts

* **VICE News Dataset**

  * **Source:** Motherboard VICE News Excel data
  * **Observations:** 3,150 entries after cleaning
  * **Features:** Date, city, Kia/Hyundai thefts, total thefts, percent Kia/Hyundai, other thefts

---

## Data Processing

Key steps included:

* Loading multiple CSV and Excel datasets into Python using Pandas
* Parsing and standardizing dates
* Renaming and cleaning columns for consistency
* Melting wide datasets into long formats for analysis
* Calculating derived metrics:

  * `total_thefts`
  * `other_thefts`
  * `percent_kia_hyundai`
* Dropping missing values where necessary
* Merging datasets to create a unified view across cities and time periods
* Preparing data for visual exploration

---

## Visualizations

Data was visualized primarily using **Seaborn** and **Matplotlib** to highlight:

* Monthly trends of Kia/Hyundai thefts by city
* Year-over-year changes in theft counts
* Proportion of Kia/Hyundai thefts relative to total vehicle thefts
* Geographic comparisons via latitude/longitude plots

All plots were static and designed for clarity in data presentation and reporting.

---

## Key Findings

* Theft rates for Kia and Hyundai vehicles vary significantly by city
* Some cities show large year-over-year increases in Kia/Hyundai thefts
* Certain regions consistently have higher percentages of Kia/Hyundai thefts relative to all vehicle thefts
* Milwaukee-specific data highlights monthly fluctuations and seasonal trends

---

## Technologies Used

* JupyterLab
* Matplotlib 
* NumPy 
* Pandas
* Python
* R (rpy2)
* Seaborn 

---

## Outputs

* Cleaned and unified datasets for Kia/Hyundai thefts across multiple cities
* Static visualizations showing trends and proportions
* Data ready for reporting, presentations, or further statistical analysis

---

## Why This Project Matters

This project highlights the value of integrating multiple real-world datasets to uncover trends in vehicle thefts. By focusing on Kia and Hyundai thefts specifically, it provides actionable insights for law enforcement, policymakers, and urban planners to better understand and respond to vehicle crime patterns.