# Predicting 30-Day Hospital Readmissions for Diabetic Patients

## Overview
This project focuses on predicting whether a diabetic patient will be readmitted to the hospital within 30 days of discharge using real-world clinical data. Hospital readmissions are costly and often indicate gaps in patient care, making accurate prediction especially important in healthcare settings where false negatives can have serious consequences.

The goal of this project was to build an interpretable classification model that prioritizes **recall**, ensuring that high-risk patients are identified and can receive preventative follow-up care.

---

## Dataset
- **Source:** UCI Machine Learning Repository  
- **Dataset:** *Diabetes 130-US Hospitals for Years 1999–2008*  
- **Size:** 101,766 patient encounters  
- **Features:** 50 variables including demographics, diagnoses, lab procedures, medications, and hospital utilization  

**Target Variable**
- `readmitted` → transformed into a binary indicator representing whether a patient was readmitted (within or after 30 days).

---

## Data Cleaning & Preparation
- Replaced missing value placeholders (`?`) with `NaN`
- Dropped features with excessive missingness or limited predictive value
- Imputed missing categorical values (race and diagnosis codes) as `"Unknown"`
- Removed identifier columns to prevent data leakage
- One-hot encoded categorical variables
- Created a binary readmission label for modeling

---

## Exploratory Data Analysis (EDA)
Key insights from the exploratory analysis:
- Average hospital stay is approximately **4 days**
- Majority of patients are over age 50
- Emergency and urgent admissions dominate the dataset
- Medication counts and length of stay show modest correlation with readmission
- Insulin prescription patterns suggest potential under-adjustment of treatment plans
- Demographic imbalance may impact model fairness

Visualizations included:
- Correlation heatmaps
- Pair plots of clinical utilization variables
- Demographic distributions (age, race, gender)
- Readmission rates by admission type and insulin status

---

## Modeling Approach
**Model:** Logistic Regression  

Logistic regression was chosen for its interpretability and suitability as a baseline model in a high-dimensional healthcare dataset.

Three model configurations were evaluated:
1. Standard Logistic Regression  
2. Class-Balanced Logistic Regression  
3. Balanced Logistic Regression with Custom Probability Thresholds  

---

## Results

| Model Variant | Recall (Readmitted) | Precision | Accuracy | ROC-AUC |
|--------------|---------------------|-----------|----------|---------|
| Standard Logistic Regression | 0.49 | 0.62 | 0.63 | 0.67 |
| Balanced Logistic Regression | 0.58 | 0.60 | 0.63 | 0.67 |
| Balanced + Threshold (0.35) | **0.89** | 0.50 | 0.55 | 0.67 |

**Key takeaway:**  
Adjusting class weights and decision thresholds significantly improved recall, capturing most potential readmissions. While precision decreased, this tradeoff is appropriate in a healthcare context where missing at-risk patients is more costly than false positives.

---

## Technologies Used
- JupyterLab
- Matplotlib
- NumPy
- Pandas
- Python
- Scikit-learn
- Seaborn

---

## Future Improvements
- Evaluate tree-based models (Random Forest, Gradient Boosting)
- Add model explainability (feature importance, SHAP)
- Address demographic imbalance with fairness-aware methods
- Incorporate temporal admission patterns

---

## Why This Project Matters
This project demonstrates applied machine learning in healthcare, emphasizing ethical tradeoffs, evaluation beyond accuracy, and decision-making under uncertainty using real-world clinical data.
