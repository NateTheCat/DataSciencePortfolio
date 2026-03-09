# Predicting Obesity Levels in Latin American Cities

## Overview

This project focuses on predicting obesity levels using demographic, dietary, and lifestyle factors collected through survey data. Obesity is associated with numerous chronic health conditions, making early identification of at-risk populations important for preventative health initiatives.

The objective of this project was to develop classification models capable of estimating obesity levels based on behavioral patterns and demographic characteristics. Two modeling scenarios were evaluated: one using both behavioral and demographic features, and another using behavioral factors alone. Comparing these scenarios helps assess how much predictive power demographic information contributes to obesity classification.

These models could be used to support **public health monitoring, early risk screening, and targeted health interventions**. For example, health organizations or local governments could use similar models to identify behavioral risk patterns within populations, design preventative education programs, or allocate resources toward communities with higher predicted obesity risk.

---

## Dataset

* **Source:** UCI Machine Learning Repository
* **Dataset:** *Estimation of Obesity Levels Based on Eating Habits and Physical Condition*
* **Observations:** 2,111 survey responses
* **Population:** Individuals from **Colombia, Peru, and Mexico**

**Features include:**

* Demographics: gender, age, height, weight
* Dietary habits: vegetable consumption, high-calorie food intake, meal frequency, snacking habits
* Lifestyle behaviors: physical activity, water intake, technology usage
* Health behaviors: calorie monitoring, alcohol consumption, smoking
* Transportation methods
* Family history of overweight

**Target Variable**

* `ObesityLevel` → categorical obesity classification including:

  * Underweight
  * NormalWeight
  * OverweightLevel1
  * OverweightLevel2
  * ObesityType1
  * ObesityType2
  * ObesityType3

---

## Data Preparation

Several preprocessing steps were applied to prepare the dataset for modeling:

* Renamed variables for improved readability and consistency
* Rounded numeric survey values to reduce synthetic noise from class-balancing samples
* Converted numerically encoded survey responses back into categorical labels
* Standardized categorical responses across multiple lifestyle variables
* Removed **height and weight** from model inputs to prevent trivial prediction of obesity levels

Two feature sets were created:

**Behavioral + Demographics**

* Includes age, gender, and behavioral lifestyle features

**Behavioral-Only**

* Excludes age and gender to evaluate prediction performance using only lifestyle factors

---

## Exploratory Data Analysis (EDA)

Exploratory analysis was conducted to better understand the distribution of obesity levels and behavioral patterns in the dataset.

Key visualizations included:

* Distribution of obesity levels across the dataset
* Age distributions by obesity category
* Relationships between obesity level and family history
* Obesity levels by high-calorie food consumption
* Lifestyle comparisons including:

  * meal frequency
  * water intake
  * physical activity
  * technology use
* Scatter plots of height versus weight by obesity category
* Age distribution histograms for each obesity class

These visualizations help highlight patterns between lifestyle behaviors and obesity classifications.

---

## Modeling Approach

This project uses **supervised classification models** to predict obesity levels.

Three classifiers were implemented:

* **Logistic Regression** – baseline linear classifier
* **Random Forest** – ensemble tree-based model capable of capturing nonlinear patterns
* **Gradient Boosting** – sequential tree-based model that improves predictive performance through boosting

A preprocessing pipeline was constructed using:

* **StandardScaler** for numeric features
* **OneHotEncoder** for categorical variables
* **ColumnTransformer** to combine transformations into a single pipeline

Models were trained and evaluated using an **80/20 train-test split** with stratified sampling to maintain class balance.

---

## Results

### Behavioral + Demographics Models

| Model               | Accuracy   |
| ------------------- | ---------- |
| Logistic Regression | 0.6170     |
| Random Forest       | **0.8274** |
| Gradient Boosting   | 0.7612     |

### Behavioral-Only Models

| Model               | Accuracy   |
| ------------------- | ---------- |
| Logistic Regression | 0.5650     |
| Random Forest       | **0.7139** |
| Gradient Boosting   | 0.6643     |

**Key Observations**

* Tree-based models significantly outperformed logistic regression.
* The **Random Forest classifier achieved the highest accuracy (82.7%)** when demographic information was included.
* Removing demographic variables reduced predictive performance but still produced reasonable results using behavioral factors alone.
* Misclassifications were most common between **adjacent obesity categories**, such as:

  * NormalWeight vs ObesityType1
  * OverweightLevel1 vs OverweightLevel2

---

## Model Insights

Feature importance analysis from the Random Forest models revealed several influential predictors.

**Behavioral-Only Model**

Top predictors included:

* Vegetable consumption frequency
* Physical activity levels
* Technology use duration
* Alcohol consumption
* Transportation method
* Meal frequency
* Water intake

**Behavioral + Demographics Model**

* **Age** emerged as the most influential feature
* Gender also contributed predictive value
* Behavioral features remained important but were more evenly distributed in importance

---

## Visualizations

Additional visualizations were created to support model interpretation:

* Model performance comparison bar charts
* Feature importance rankings for both modeling scenarios
* Confusion matrix heatmaps for each classifier
* Class-level accuracy comparisons between feature sets

These visualizations provide insights into classification performance and highlight where prediction improvements occur when demographic information is included.

---

## Technologies Used

* JupyterLab
* Matplotlib
* NumPy
* Pandas
* Python
* Scikit-learn
* Seaborn

---

## Why This Project Matters

Obesity continues to be a growing public health concern in many parts of the world, including Latin America. Predictive models like those developed in this project can help researchers and policymakers better understand how lifestyle behaviors influence obesity risk within populations.

In practical settings, similar models could be used to:

* Support **population-level health monitoring**
* Identify **behavioral risk patterns associated with obesity**
* Guide **preventative health campaigns and education programs**
* Assist researchers studying **lifestyle and demographic drivers of obesity**

While behavioral data alone provides a reasonable baseline for obesity prediction, incorporating demographic information significantly improves classification accuracy. These findings highlight how combining lifestyle patterns with demographic context can enhance predictive health analytics while still allowing behavioral-only models to support broader community-level assessments.