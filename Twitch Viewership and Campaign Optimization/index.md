# Optimizing Sponsored Content on Twitch: Game and Viewership Trends

## Overview

This project analyzes historical Twitch viewership trends to identify patterns in game popularity, platform engagement, and opportunities for sponsored content. The analysis combines multiple datasets of game-level and platform-level metrics to examine monthly trends, top-performing games, and the proportion of total viewership contributed by leading games.

---

## Datasets

* **Twitch Game Data**

  * **Source:** Kaggle – Twitch Analytics
  * **Observations:** 21,000 monthly game-level records (2016–mid-2024)
  * **Features:** `Rank`, `Game`, `Month`, `Year`, `Hours_watched`, `Hours_streamed`, `Peak_viewers`, `Peak_channels`, `Streamers`, `Avg_viewers`, `Avg_channels`, `Avg_viewer_ratio`

* **Twitch Platform Data**

  * **Source:** Kaggle – Twitch Analytics
  * **Observations:** 105 monthly platform-level records
  * **Features:** `Year`, `Month`, `Hours_watched`, `Avg_viewers`, `Peak_viewers`, `Streams`, `Avg_channels`, `Games_streamed`, `Viewer_ratio`

---

## Data Processing

Key steps included:

* Loading CSV files into Python using Pandas
* Cleaning non-Latin and accented characters in game titles
* Converting `Year` and `Month` into datetime objects for time-series analysis
* Aggregating game-level data to identify top games by total hours watched and peak viewers
* Calculating rolling 6-month averages to smooth short-term spikes
* Merging game-level and platform-level datasets for comparative analysis
* Computing derived metrics such as top games’ share of total platform viewership

---

## Visualizations

Data was visualized using **Seaborn** and **Matplotlib** to highlight:

* Monthly and yearly trends in hours watched and peak viewers
* Distribution and variability of key metrics (`Hours_watched`, `Hours_streamed`, `Avg_viewer_ratio`)
* Seasonal patterns in viewership
* Top 10–15 games’ contribution to overall platform engagement
* Rolling averages to identify long-term trends
* Scatterplots and correlation heatmaps to explore relationships between metrics

All plots are static, designed for clear presentation of insights.

---

## Key Findings

* A small number of games dominate Twitch viewership, suggesting high-impact targets for sponsorships
* Average viewers per channel remain relatively stable, even as total viewership fluctuates
* Platform engagement grew steadily from 2016–2021, with seasonal peaks in spring and summer months
* Top-performing games account for a significant portion of platform viewership, but their share fluctuates over time
* Short-term spikes in game popularity present opportunities for quick, targeted campaigns

---

## Technologies Used

* JupyterLab
* Matplotlib
* NumPy
* Pandas
* Python
* Seaborn

---

## Outputs

* Cleaned, unified datasets for Twitch game- and platform-level metrics
* Static visualizations showing trends, distributions, and correlations
* Comparative analysis of top games versus total platform engagement
* Insights ready for presentations, reporting, or further modeling

---

## Why This Project Matters

This project demonstrates **data-driven insights for digital marketing and sponsorship strategy**. By analyzing historical Twitch metrics, it helps marketers, advertisers, and platform partners identify:

* Optimal timing for campaigns
* Games with consistent high viewership for long-term promotion
* Opportunities to leverage short-term spikes in popularity