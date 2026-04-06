# Project 13: Unsupervised Customer Segmentation
**Mintay Misgano | People Analytics Portfolio**

---

## What I Did

Applied four unsupervised clustering algorithms to a credit card applicant dataset (N = 1,319) to identify behaviorally distinct customer profiles — without using approval status as a target. Features: income, monthly expenditure, spending share, age, account tenure, active accounts, and derogatory reports.

Methods: **K-Means** (elbow-selected K = 4) · **Hierarchical/Ward's D2** · **DBSCAN** · **Mean Shift**

---

## Key Finding

Four applicant profiles emerge consistently across all methods:

| Segment | Profile | Approval Rate |
|---------|---------|--------------|
| Low-Utilization | Minimal spend, short tenure, limited credit history | Moderate |
| High-Spend Established | High income, elevated expenditure, long tenure | High |
| High-Risk Delinquency | Above-avg derogatory reports, high spend-to-income ratio | Low |
| Young Active Spenders | Younger, moderate income, high active account count | Moderate–High |

Hierarchical clustering converged with K-Means (Adjusted Rand Index > .60). DBSCAN flagged ~5% of applicants as noise — profiles too atypical for clean segment assignment, ideal candidates for manual underwriter review.

---

## Why It Matters

Multi-method convergence is the key signal here. When K-Means, hierarchical, density-based, and mode-seeking algorithms independently recover the same four segments, that structure is real — not an artifact of any one algorithm's assumptions. The same framework applies to People Analytics: employee experience profiling, turnover risk segmentation, or compensation equity clustering all benefit from this cross-method validation approach.

---

## Files

| File | Description |
|------|-------------|
| `01_credit_card.csv` | Dataset (N = 1,319, 12 features) |
| `02_Clustering_Analysis_R.md` | Full R analysis — all four clustering methods with elbow plots, dendrograms, and cluster profiles |
| `03_Project_Report.md` | Full APA-style report with results, discussion, and references |

---

*Data: CreditCard dataset (Greene, 2003) · R (cluster, dbscan, meanShiftR, factoextra)*
