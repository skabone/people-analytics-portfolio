# Project 06 — Kaggle Titanic ML Classification

**Best Kaggle Score:** 0.79186 (public leaderboard, top ~22%) | 5-model hard-voting ensemble

---

## Overview

Classic binary classification competition: predict passenger survival on the Titanic using demographic and ticket features. This project implements a complete ML pipeline — feature engineering, multi-model training, cross-validated evaluation, and ensemble voting — demonstrating skills directly applicable to people analytics prediction tasks (attrition, flight risk, candidate scoring).

---

## Results

| Submission | Method | Kaggle Score |
|:-----------|:-------|:------------:|
| 1 | Single Decision Tree (baseline) | 0.76555 |
| 2 | 3-model voting ensemble | 0.77511 |
| 3 | 5-model voting ensemble | 0.78947 |
| **4 (Best)** | **5-model ensemble (tuned)** | **0.79186** |

---

## Pipeline

```
Raw Data → Feature Engineering → Individual Models → Cross-Validation → Voting Ensemble → Submission
```

**Feature engineering highlights:**
- Title extracted from passenger names → used for age imputation by (Title × Pclass) subgroup
- Family size (SibSp + Parch + 1) and solo-traveler flag
- Fare log-transformation to reduce skew
- HasCabin flag (proxy for first-class proximity to lifeboats)
- Age bands (ordinal discretization)

**Classifiers in voting ensemble:**
- Logistic Regression
- Gaussian Naive Bayes
- Decision Tree
- Random Forest
- Gradient Boosting

---

## Files

| File | Description |
|:-----|:------------|
| `Titanic_ML_Classification.py` | Complete pipeline: feature engineering, model training, CV evaluation, ensemble, submission |
| `Titanic_Project_Report.md` | Full written report with methods, results, and people analytics transfer |
| `Executive_Brief.md` | 1-page practitioner summary |

**Note:** Data files (`train.csv`, `test.csv`) are in `../data/`. The script uses relative paths.

---

## Tools

- **Language:** Python
- **Libraries:** scikit-learn, pandas, numpy
- **Methods:** Logistic Regression, Naive Bayes, Decision Tree, Random Forest, Gradient Boosting, hard-voting ensemble, stratified 5-fold CV, feature importance (Gini)

---

*Part of the [People Analytics Portfolio](../README.md) | Analyst: Mintay Misgano | Course: ISM 6359 Data Mining, SPU (Winter 2022)*
