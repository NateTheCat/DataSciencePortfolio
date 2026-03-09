# Fair Pricing Predictions in the Used Car Market

## Overview

This project analyzes a large used vehicle sales dataset to build predictive models that estimate **fair vehicle selling prices**. The analysis includes extensive data cleaning, feature engineering, and model comparison using multiple regression techniques to ensure that price predictions are realistic and unbiased.

The primary objective was to understand which features influence vehicle prices and to develop models that provide **accurate, equitable estimates** while avoiding data leakage caused by pre-existing estimated price variables.

The project demonstrates an end-to-end data mining workflow, including exploratory data analysis, data preparation, feature encoding, and predictive modeling, aimed at **empowering buyers and sellers with fair market insights**.

---

## Dataset

**Source:** Used car auction dataset

**Observations:** ~558,000 vehicle sales records
**Final cleaned dataset:** 544,188 records

**Features:** 16 original variables including:

* Vehicle information (year, make, model, trim, body)
* Vehicle condition and mileage
* Location and seller information
* Interior and exterior color
* Transmission type
* Estimated market price (MMR)
* Final selling price

Key variables used for modeling:

* Vehicle year
* Vehicle condition
* Odometer reading
* Make, model, trim
* Body type
* Transmission
* State
* Interior and exterior color
* Engineered feature: vehicle age

Target variable:

* **Selling Price** – used as a proxy for **fair market value**

---

# Exploratory Data Analysis

Several visualizations were created to better understand relationships between vehicle features and selling price. This analysis helps identify **factors that contribute to fair pricing**.

### Selling Price by Model Year

Boxplots revealed that newer model years generally have higher selling prices, but luxury brands and high-performance trims introduce significant outliers. Understanding these patterns is critical for **avoiding over- or underestimation**.

### Selling Price by Vehicle Condition

Average selling prices increase as condition ratings improve, although the dataset revealed multiple condition rating scales. Normalizing these ratings helps ensure **consistent, fair price estimates**.

### Correlation Analysis

A correlation heatmap showed:

* Strong correlation between **MMR and selling price**
* Negative correlation between **odometer and vehicle year**
* Moderate correlation between **vehicle year and price**

These observations suggested that additional categorical variables (make, model, trim) could significantly influence price predictions while maintaining fairness.

### Scatterplot Matrix

Pairwise feature comparisons helped visualize relationships between numerical variables and confirmed correlations observed in the heatmap.

---

# Data Processing

## Feature Removal

Certain variables were removed due to lack of predictive value:

* **VIN** – unique identifier
* **Seller** – business names without useful categorization

The **MMR (Manheim Market Report)** variable was initially retained for comparison but later removed to prevent data leakage and ensure **models reflect fair pricing based on real vehicle characteristics**.

---

## Feature Engineering

### Vehicle Age

A new feature was created to better capture depreciation effects:

Vehicle Age = Sale Year − Model Year

This provides a more meaningful representation of how vehicle age affects price, ensuring **equitable estimation across vehicles of different ages**.

---

## Data Cleaning

### Condition Normalization

The dataset contained multiple condition rating scales (1–5 and 1–50). Values were normalized to a **standard 1–5 scale** to support **consistent and fair price predictions**.

### Categorical Standardization

Several categorical variables required cleaning:

* **Make**
* **Model**
* **Trim**
* **Body**
* **Transmission**
* **State**
* **Color**
* **Interior**

Common fixes included:

* Converting text to lowercase
* Removing whitespace inconsistencies
* Correcting spelling variations
* Consolidating proprietary body types into standardized categories
* Removing extremely rare categories to reduce noise

---

# Handling Missing Data

Missing values ranged from **0.02% to 11.6%** across columns.

A custom imputation function was developed that filled missing values using the **most common value among similar vehicles**, grouped by relevant features, to maintain **fairness across similar vehicle types**.

Example imputation strategies:

| Feature      | Imputation Strategy                             |
| ------------ | ----------------------------------------------- |
| Transmission | Grouped by make, model, trim                    |
| Color        | Grouped by make, model, trim                    |
| Interior     | Grouped by make, model, trim                    |
| Condition    | Grouped by make, model, odometer or vehicle age |
| Body         | Grouped by make, model, trim                    |

After imputation and removal of minimal remaining null rows, the final dataset contained **544,188 complete records**.

---

# Feature Encoding

Because the dataset contains many categorical features, one-hot encoding was applied using `pd.get_dummies()`.

Categorical variables encoded:

* Make
* Model
* Trim
* Body
* Transmission
* State
* Color
* Interior

This expanded the dataset to:

* **1,822 total features**
* ~1GB in memory after encoding

---

# Modeling

Three regression approaches were used to predict **fair vehicle selling prices**:

* Linear Regression
* Ridge Regression
* Lasso Regression

Data was split into **80% training and 20% testing sets**.

Feature scaling was applied using `StandardScaler` to ensure stable coefficient estimates.

---

## Model Comparison

Two modeling scenarios were evaluated:

### Model Including MMR

The MMR column (market price estimate) was included as a feature.

Results:

* **R² ≈ 0.97**
* Very low prediction error

However, coefficient analysis revealed that the model relied heavily on MMR, indicating **data leakage** and reduced transparency in pricing fairness.

---

### Model Without MMR

After removing the MMR column, the model relied on actual vehicle characteristics such as:

* Condition
* Vehicle age
* Odometer
* Make and model
* Geographic location

This produced more realistic performance and better reflected **equitable price determination**, free from bias introduced by pre-existing market estimates.

---

# Key Insights

* **Vehicle age and condition** are strong predictors of resale value.
* **Odometer readings** correlate with depreciation but vary significantly by vehicle type.
* **Vehicle make and model** introduce large price variation due to brand and trim differences.
* Pre-existing price estimates such as **MMR can artificially inflate model accuracy**, highlighting the importance of **fair and transparent modeling**.

---

# Technologies Used

* JupyterLab
* Matplotlib
* NumPy
* Pandas
* Python
* Scikit-learn
* Seaborn

---

# Outputs

* Exploratory visualizations
* Cleaned and engineered dataset
* Regression model comparisons
* Model evaluation metrics (MAE, MSE, RMSE, R²)

---

# Why This Project Matters

This project demonstrates the complete **data mining pipeline required for real-world predictive modeling**, including large-scale data cleaning, feature engineering, categorical encoding, and regression analysis.