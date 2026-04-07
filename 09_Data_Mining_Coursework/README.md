# Project 09 - Job Change Prediction with CRISP-DM

Author: Mintay Misgano, PhD

This project applies the CRISP-DM framework to a public Kaggle dataset on job-change intent among data science trainees. The package is organized as a compact end-to-end classification workflow, from business framing and data preparation through model comparison and evaluation.

## What This Project Demonstrates

- Use of CRISP-DM as a structured workflow for an applied machine learning project
- Cleaning and feature engineering for a moderately large tabular dataset
- Comparison of multiple classification models under a shared cross-validation setup
- Use of ROC-AUC alongside accuracy for an imbalanced binary outcome

## Main Results

- Gradient boosting produced the strongest overall model performance in this workflow.
- Ensemble methods outperformed simpler single-model baselines.
- City development index, experience, and company-related features were among the strongest predictors.
- ROC-AUC was a more informative success metric than accuracy alone because the positive class was the minority class.

## Read This Project

- Start with [Job_Change_Prediction_Project_Summary.md](/Users/Taco/Library/CloudStorage/ProtonDrive-Skabone@pm.me-folder/2!!Career/GitHub_Portfolio/09_Data_Mining_Coursework/GitHub_Ready/Job_Change_Prediction_Project_Summary.md) for the short overview.
- Use [Job_Change_Prediction_Project_Report.md](/Users/Taco/Library/CloudStorage/ProtonDrive-Skabone@pm.me-folder/2!!Career/GitHub_Portfolio/09_Data_Mining_Coursework/GitHub_Ready/Job_Change_Prediction_Project_Report.md) for the fuller CRISP-DM write-up.
- See [Job_Change_Prediction_Data_Mining.py](/Users/Taco/Library/CloudStorage/ProtonDrive-Skabone@pm.me-folder/2!!Career/GitHub_Portfolio/09_Data_Mining_Coursework/GitHub_Ready/Job_Change_Prediction_Data_Mining.py) for the implementation.

## Data Note

The project uses Kaggle's HR Analytics: Job Change of Data Scientists dataset. It is best read as a benchmark-style applied data-mining project that demonstrates workflow, feature preparation, and model evaluation rather than a production deployment claim.
