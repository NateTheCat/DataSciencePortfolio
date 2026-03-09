# Predicting Sleep Quality from Lifestyle Factors

## Overview

This project explores the relationship between sleep quality, physical activity, stress levels, and other lifestyle factors using statistical analysis and machine learning techniques.

The analysis includes exploratory data analysis, hypothesis testing, regression modeling, classification models, and clustering to better understand which factors influence sleep quality. The project demonstrates a full data science workflow from data exploration through predictive modeling.

---

## Dataset

**Source:** Sleep Health and Lifestyle Dataset

**Observations:** 374 individuals

**Features:** 13 variables describing demographic, health, and lifestyle characteristics.

Key variables include:

* **Age:** Age of the individual
* **Gender:** Male or Female
* **Occupation:** Profession of the individual
* **Sleep Duration:** Average hours slept per day
* **Quality of Sleep:** Self-reported score from 1–10
* **Physical Activity Level:** Minutes of activity per day
* **Stress Level:** Self-reported stress score (1–10)
* **BMI Category:** Underweight, Normal, Overweight, or Obese
* **Blood Pressure:** Systolic/diastolic measurement
* **Heart Rate:** Resting heart rate (bpm)
* **Daily Steps:** Number of steps per day
* **Sleep Disorder:** Presence of insomnia or sleep apnea

The **Person ID** column was removed during preprocessing because it does not contribute to the analysis.

---

## Exploratory Data Analysis

### Univariate Analysis

Descriptive statistics were computed for all numerical variables, including:

* Mean
* Standard deviation
* Minimum and maximum values
* Skewness
* Kurtosis

Histograms and boxplots were generated to examine the distributions of:

* Age
* Sleep duration
* Sleep quality
* Physical activity level
* Stress level
* Heart rate
* Daily steps

These visualizations helped identify potential skewness, spread, and outliers within the dataset.

---

### Bivariate Analysis

Pearson correlation was used to examine relationships between numerical variables.

A correlation heatmap revealed several notable relationships:

* **Sleep Duration and Quality of Sleep:** strong positive correlation
* **Stress Level and Sleep Quality:** strong negative correlation
* **Physical Activity and Daily Steps:** strong positive correlation
* **Heart Rate and Stress Level:** moderate positive correlation

A Seaborn **pairplot** was also generated to visually explore relationships between all numerical variables.

---

## Statistical Testing

A hypothesis test was performed to evaluate the relationship between **physical activity level and sleep quality**.

**Null Hypothesis (H₀):**
There is no significant relationship between physical activity and sleep quality.

**Alternative Hypothesis (H₁):**
There is a significant relationship between physical activity and sleep quality.

Because the variables were not perfectly normally distributed, a **Spearman correlation test** was used.

**Results:**

* Spearman correlation: **0.178**
* p-value: **0.0005**

Since the p-value is below 0.05, the null hypothesis was rejected, indicating a **statistically significant positive relationship** between physical activity and sleep quality, although the strength of the relationship is relatively weak.

---

## Regression Analysis

A **linear regression model** was used to examine how physical activity predicts sleep quality.

Key results:

* **Intercept:** ~6.66
* **Coefficient:** ~0.011
* **R²:** 0.037

Interpretation:

* Each additional minute of physical activity is associated with a small increase in sleep quality.
* The low R² suggests that **physical activity alone explains only about 3.7% of sleep quality variation**, indicating that other factors likely influence sleep outcomes.

A scatter plot with a regression line was created to visualize the relationship between physical activity and sleep quality.

---

## Classification Models

Sleep quality scores were treated as classification categories and predicted using two machine learning models.

### Logistic Regression

Features used:

* Physical Activity Level
* Sleep Duration

Model results:

* **Accuracy:** 83%
* Strong predictions for sleep scores **6, 8, and 9**
* Lower performance for scores **4 and 5** due to small sample sizes

A confusion matrix was visualized using a **Seaborn heatmap**.

---

### Random Forest Classification

A Random Forest classifier was implemented using the same features.

Results improved significantly compared to logistic regression:

* **Accuracy:** 91%
* Higher recall and precision across most sleep score categories
* Improved performance for score **7**, which logistic regression struggled to classify

The Random Forest model performed better due to its ability to capture **nonlinear relationships and handle class imbalance more effectively**.

---

## Clustering Analysis

K-Means clustering was used to group individuals based on:

* Physical activity level
* Sleep quality

Four clusters were identified.

Cluster interpretations:

* **Cluster 0:** Moderate-high activity with highest sleep quality
* **Cluster 1:** Very high activity with strong sleep quality
* **Cluster 2:** Low activity with moderate sleep quality
* **Cluster 3:** Low-moderate activity with lowest sleep quality

The clustering produced a **silhouette score of 0.71**, indicating well-separated clusters.

---

## Technologies Used

* JupyterLab
* Matplotlib
* NumPy
* Pandas
* Python
* Scikit-learn
* SciPy
* Seaborn

---

## Key Findings

* Sleep duration is strongly correlated with sleep quality.
* Stress levels have a strong negative relationship with sleep quality.
* Physical activity shows a statistically significant but relatively weak relationship with sleep quality.
* Random Forest classification significantly improved predictive accuracy compared to logistic regression.
* Clustering analysis identified meaningful groups based on physical activity and sleep patterns.

---

## Why This Project Matters

Sleep health is closely connected to lifestyle behaviors such as physical activity, stress management, and daily habits. This project demonstrates how statistical analysis and machine learning can be used to identify patterns in health data and better understand the factors influencing sleep quality.