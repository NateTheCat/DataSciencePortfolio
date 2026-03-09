# Modeling Steam Game Prices for Indie Developers

## Overview

This project focuses on estimating baseline prices for Steam games, helping indie and small development teams make informed pricing decisions. Without access to market research or publisher support, developers may struggle to price games fairly—too high can discourage buyers, while too low can undervalue their work.

The goal of this project was to build predictive regression models that use game characteristics (genres, categories, release timing) and, optionally, publisher context to provide **baseline pricing guidance** for developers.

---

## Dataset

* **Source:** [Kaggle – Steam Games Dataset (2021–2025)](https://www.kaggle.com/datasets/jypenpen54534/steam-games-dataset-2021-2025-65k)
* **Size:** ~65,000 games
* **Features:**

  * `appid` → Unique game ID
  * `name` → Game title
  * `release_date` → Release date
  * `price` → Listed price in USD
  * `genres` → Game genres (multi-label)
  * `categories` → Game features (e.g., single-player, controller support)
  * `developer` → Game developer
  * `publisher` → Game publisher
  * `recommendations` → Number of user recommendations

**Target Variable**

* `price` → Continuous numeric variable representing the game’s price

---

## Data Cleaning & Preparation

* Removed outliers (games priced above $70)
* Filled missing genre, category, and publisher information
* Converted multi-label `genres` and `categories` to binary features using one-hot encoding
* Created numeric features: number of genres, number of categories, release month, and season
* Grouped rare publishers under “Other” to reduce sparsity
* Used sparse matrices to efficiently handle high-dimensional categorical features

---

## Exploratory Data Analysis (EDA)

Key insights:

* Certain genres (e.g., Action, RPG) tend to have higher prices
* Free-to-play titles are present but relatively rare
* User recommendations loosely correlate with price
* Release month and season show minor effects on pricing trends

Visualizations included:

* Price distributions by genre and category
* Scatterplots of price vs. recommendations
* Heatmaps of genre and category co-occurrence
* Boxplots comparing pricing by publisher

---

## Modeling Approach

**Models:** Ridge Regression, Random Forest, Gradient Boosting, LightGBM

Two scenarios were evaluated:

1. **No-Publisher Model** – simulates self-published or first-time developers; uses only game attributes (genres, categories, release features).
2. **Publisher-Aware Model** – simulates games released through established publishers; incorporates publisher, release year, and recommendation counts in addition to game attributes.

**Evaluation Metrics:**

* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)
* R² Score
* Mean Absolute Percentage Error (MAPE)

---

## Results

### No-Publisher Model

| Model             | MAE ($) | RMSE ($) | R²    | MAPE (%) |
| ----------------- | ------- | -------- | ----- | -------- |
| Ridge Regression  | 4.37    | 6.86     | 0.254 | 152.3    |
| Random Forest     | 3.83    | 6.40     | 0.350 | 108.7    |
| Gradient Boosting | 4.03    | 6.54     | 0.323 | 124.7    |
| LightGBM          | 3.88    | 6.36     | 0.359 | 114.3    |

### Publisher-Aware Model

| Model             | MAE ($) | RMSE ($) | R²    | MAPE (%) |
| ----------------- | ------- | -------- | ----- | -------- |
| Ridge Regression  | 4.49    | 7.01     | 0.222 | 159.9    |
| Random Forest     | 3.64    | 6.02     | 0.425 | 110.2    |
| Gradient Boosting | 3.75    | 6.05     | 0.421 | 120.9    |
| LightGBM          | 3.66    | 6.07     | 0.415 | 111.3    |

**Key takeaway:**

* Tree-based models (Random Forest, LightGBM) outperform linear regression in both scenarios.
* Publisher and recommendation data significantly improve predictive performance.
* No-Publisher models provide a conservative, realistic baseline for indie developers with limited information.

---

## Technologies Used

* JupyterLab
* LightGBM
* Matplotlib
* NumPy
* Pandas
* Python
* Scikit-learn 
* Seaborn

---

## Future Improvements

* Incorporate time-series pricing and sales data
* Develop genre-specific pricing models
* Recommend price ranges instead of single price points
* Evaluate model explainability (feature importance, SHAP)

---

## Why This Project Matters

This project demonstrates applied machine learning for business decision-making in the gaming industry. It highlights how structured historical data can inform fair pricing, particularly for independent developers, while emphasizing **ethical use** of predictive models to avoid pressuring developers toward market averages.