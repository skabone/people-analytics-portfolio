# Project 05 — Psychometric Scale Validation (R)

**Complete validation workflow:** reliability → item analysis → exploratory factor analysis applied to the LGBTQ College Campus Climate Scale (N = 646 simulated observations)

---

## Overview

This project demonstrates a full psychometric scale validation pipeline in R. Using the Perceptions of the LGBTQ College Campus Climate Scale (Szymanski & Bissonette, 2020) as the demonstration instrument, the analysis validates a theorized two-factor structure — **College Response** and **Stigma** subscales — through four independent stages of evidence.

Item-level data are simulated directly from published factor loadings, means, and sample size, making the analysis fully transparent and reproducible without requiring access to proprietary data.

---

## Key Results

| Scale              | α     | Avg inter-item *r* | Factor loadings (range) |
|:-------------------|:-----:|:------------------:|:-----------------------:|
| Total (6 items)    | .64   | .23                | —                       |
| College Response   | .79   | .56                | .73–.88                 |
| Stigma             | .79   | .56                | .71–.86                 |

- All 6 items show corrected item-total correlations of .59–.69 with their own subscale
- Cross-subscale discriminant correlations: |*r*| ≤ .13 in all cases
- Both PCA and PAF recover an identical two-factor solution; between-factor *r* ≈ .00
- Parallel analysis confirms retention of exactly two factors

---

## Validation Workflow

```
Data Simulation (from published parameters)
        ↓
Reverse Scoring + Scale Scoring (AIA approach)
        ↓
Reliability Analysis
  ├── Cronbach's alpha (α) — total + subscales
  └── McDonald's omega (ωt, ωh) — total scale
        ↓
Item Analysis
  ├── Corrected item-total correlations (r.drop)
  └── Cross-subscale discriminant validity
        ↓
Exploratory Factor Analysis
  ├── Suitability: Bartlett's test + KMO
  ├── Retention: Scree plot + Parallel analysis
  ├── PCA: orthogonal (varimax) + oblique (oblimin)
  └── PAF: orthogonal (varimax) + oblique (oblimin)
```

---

## Files

| File | Description |
|:-----|:------------|
| `Psychometrics_Scale_Validation.Rmd` | Full annotated R Markdown — renders to GitHub-viewable `.md` |
| `Psychometrics_Project_Report.md` | PhD-quality narrative report with results, tables, and discussion |
| `Executive_Brief.md` | 1-page non-technical summary for practitioners and hiring managers |

---

## Tools & Packages

- **Language:** R
- **Core packages:** `psych` (reliability, omega, EFA), `tidyverse` (data wrangling), `MASS` (data simulation), `sjstats` (AIA scale scoring), `apaTables` (APA-formatted correlation tables)
- **Methods:** Cronbach's α, McDonald's ω, corrected item-total correlations, PCA, PAF, varimax and oblimin rotation, parallel analysis

---

## How to Run

1. Open `Psychometrics_Scale_Validation.Rmd` in RStudio
2. All data are simulated within the script — no external data file required
3. Knit to `github_document` to produce the GitHub-renderable `.md` output

---

*Part of the [People Analytics Portfolio](../README.md) | Analyst: Mintay Misgano*
