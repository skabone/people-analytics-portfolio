# IBM Employee Attrition Analysis — Project Summary

**Dataset:** IBM HR Analytics public benchmark  
**Scope:** Attrition pattern analysis and model comparison

---

## Project Context

This project was completed as part of graduate coursework in people analytics and machine learning. It uses a public benchmark dataset to examine which workforce factors are associated with attrition and to compare several standard classification models in a structured workflow.

The goal is to demonstrate how an attrition analysis can be framed, modeled, and interpreted responsibly using public data.

---

## What Was Done

- Analyzed 1,470 employee records across demographic, job, compensation, satisfaction, and tenure variables
- Examined attrition patterns with exploratory visual analysis
- Addressed class imbalance, since attrition represents about 16% of the dataset
- Compared Logistic Regression, Decision Tree, and Random Forest performance
- Used PCA as a supplementary step to explore structure in the feature set

---

## Main Takeaways

- **Overtime stands out as a major attrition signal.** Employees working overtime show notably higher attrition rates in the benchmark data.
- **Compensation-related variables matter.** Monthly income and stock option level appear near the top of the feature rankings in tree-based models.
- **Risk is not evenly distributed across groups.** Younger employees, single employees, and some job roles show higher attrition patterns than others.
- **Modeling performance improved once class imbalance was handled.** This reinforces how important minority-class treatment is in attrition work.
- **Logistic Regression performed best in this project setup.** It achieved the strongest overall test metrics, including AUC = 0.934.

---

## What This Demonstrates

For a real organization, these results point to several areas worth validating with internal data:

1. Overtime and workload patterns as potential retention risks
2. Compensation and equity structure as possible differentiators in exit risk
3. Early-tenure experience as a priority window for retention analysis
4. Role-specific attrition patterns rather than one-size-fits-all interventions

These are illustrative implications, not deployment recommendations. Any operational use would require organization-specific data, validation, fairness review, and stakeholder review.

---

## Bottom Line

This project shows a practical people analytics workflow for attrition modeling: define the business question, inspect the data carefully, account for class imbalance, compare multiple models, and translate findings into cautious business implications. The strongest value here is the demonstration of analytical skill: moving from raw benchmark data to interpretable results without overstating what the data can support.
