# HR Employee Attrition Analysis — IBM Dataset

**Author:** Mintay Misgano, Ph.D.
**Focus:** People Analytics | I-O Psychology | Workforce Modeling
**Dataset:** [IBM HR Analytics Employee Attrition & Performance](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) (Kaggle)

---

## Overview

Employee attrition is one of the most costly challenges in workforce management. This project analyzes IBM's HR dataset (1,470 employees, 35 variables) to identify the key drivers of voluntary turnover and build a predictive classification model for attrition risk.

**Business Question:** What employee characteristics and work conditions are most associated with attrition, and can we predict which employees are at highest risk?

---

## Notebooks

| # | Notebook | Description |
|---|----------|-------------|
| 01 | `01_EDA_and_Preprocessing.ipynb` | Data exploration, class imbalance analysis, visualizations, SMOTE/ADASYN oversampling |
| 02 | `02_Decision_Tree_Modeling.ipynb` | Decision Tree and Random Forest classifiers, feature importance, model evaluation |
| 03 | `03_PCA_Analysis.ipynb` | Dimensionality reduction with and without standardization |

---

## Key Findings

- Attrition base rate is ~16%, creating a class imbalance that required oversampling (SMOTE/ADASYN) before modeling
- Overtime, job role, marital status, and distance from home were among the strongest visual predictors of attrition
- Decision Tree and Random Forest models were compared across original and balanced datasets
- PCA was used to explore whether dimensionality reduction improved model separability

---

## Tools & Methods

- **Python:** pandas, numpy, scikit-learn, seaborn, matplotlib, statsmodels
- **Models:** Decision Tree Classifier, Random Forest Classifier
- **Preprocessing:** Label encoding, feature scaling, train/test split
- **Imbalance handling:** SMOTE (Synthetic Minority Oversampling Technique), ADASYN
- **Dimensionality reduction:** PCA with and without standardization

---

## Data

`HR_Attrition_IBM.csv` — original Kaggle dataset, 1,470 rows × 35 columns. No missing values.

---

## About

This project was completed as part of graduate coursework in People Analytics and Machine Learning at Seattle Pacific University (2022). The methods applied here — classification modeling, feature engineering, and imbalance handling — are directly relevant to real-world workforce analytics use cases such as retention risk scoring, workforce planning, and HRIS analytics.

*Ph.D. in Industrial-Organizational Psychology, Seattle Pacific University (2026)*
