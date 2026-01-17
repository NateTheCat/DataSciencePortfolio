# Visualizing Childcare Affordability Across the United States

## Overview
This project analyzes childcare affordability across the United States by examining how much of a household’s income is spent on childcare for infants, toddlers, and preschool-aged children.

The analysis combines data wrangling, static visualizations, and interactive mapping to highlight regions where childcare costs exceed commonly recommended affordability thresholds (7%–10% of household income).

---

## Dataset
- **Source:** National Database of Childcare Prices  
- **Observations:** 34,567 county-level records  
- **Features:** 227 variables including childcare prices, income levels, geography, and year  

Derived metrics:
- Monthly childcare costs by age group
- Monthly household income
- Percentage of households exceeding affordability thresholds

---

## Data Processing
Key transformations included:
- Converting weekly childcare costs to monthly estimates
- Cleaning and converting household income values
- Calculating childcare cost as a percentage of income
- Creating affordability indicators based on 7% and 10% thresholds
- Aggregating results by state and year for visualization

---

## Interactive Visualization
An interactive, animated choropleth map was created using Plotly to display:
- Percentage of households spending more than 10% of income on childcare
- State-level comparisons across years
- Differences by childcare age group

The visualization allows users to:
- Hover for detailed state-level information
- Animate trends over time
- Compare affordability patterns geographically

The final map was exported as a standalone HTML file for web embedding.

---

## Static Visualizations
Additional visual analysis includes:
- Distributions of monthly childcare costs by age group
- Boxplots comparing childcare costs to income thresholds
- Scatter plots of household income versus infant care cost
- Histograms of childcare cost as a percentage of income
- State-level bar charts of average childcare costs
- Line charts showing trends over time

These plots provide complementary perspectives on affordability and regional disparities.

---

## Key Findings
- Infant care is consistently the most expensive form of childcare
- Many states exceed the 10% affordability threshold for a large share of households
- Lower-income regions are disproportionately affected
- Childcare costs have steadily increased over time across all age groups

---

## Technologies Used
- JupyterLab
- Matplotlib
- NumPy
- Pandas
- Plotly
- Python
- Seaborn

---

## Outputs
- Interactive HTML choropleth map
- Static visualizations and infographic summarizing results

---

## Why This Project Matters
This project demonstrates effective data storytelling through visualization, transforming complex socioeconomic data into accessible insights relevant to policy, economics, and public planning.
