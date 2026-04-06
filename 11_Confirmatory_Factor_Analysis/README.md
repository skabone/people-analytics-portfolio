# Confirmatory Factor Analysis: Scale Validation of the GRMSAAW

**People Analytics | Psychometrics & Measurement Validation**
**Tools:** R (`lavaan`, `semPlot`, `psych`) · Python (`semopy`, `pandas`, `matplotlib`)
**Dataset:** Simulated from Keum et al. (2018) · N = 304 · 22 items · 4 subscales

---

## Why This Project Matters

Before any survey instrument can produce trustworthy organizational insights, its measurement structure must be validated. A scale that claims to measure four distinct constructs but actually functions as a single composite score will produce misleading data and misdirected action — a particularly high-stakes problem in DEI measurement, where decisions about underrepresented groups depend on measurement accuracy.

This project applies **Confirmatory Factor Analysis (CFA)** to the *Gendered Racial Microaggressions Scale for Asian American Women* (GRMSAAW; Keum et al., 2018), formally testing whether the instrument's four-subscale structure is empirically supported or whether the data are better explained by a single general factor. The analysis is implemented in both **R** and **Python**, with identical χ² results confirming cross-platform accuracy.

---

## Key Results

| Fit Index | Unidimensional Model | **Four-Factor Model** | Benchmark |
|---|:---:|:---:|---|
| CFI | .578 | **.991** | ≥ .95 |
| RMSEA | .112 [.105, .119] | **.017 [.000, .031]** | ≤ .05 |
| SRMR | .124 | **.058** | < .10 |
| AIC | 17,755 | **16,984** | lower = better |
| BIC | 17,919 | **17,170** | lower = better |
| Δχ²(6) | — | **783.28, *p* < .001** | significant = preferred |

The four-factor correlated model is **unambiguously superior** on every criterion. All 22 factor loadings are statistically significant (standardized range: .35–.82). The four subscales are distinct but mildly correlated (*r* < .10), confirming they represent related yet separable dimensions of microaggression experience.

---

## The Instrument

The GRMSAAW (Keum et al., 2018) assesses how frequently Asian American women encounter gendered racial microaggressions. Items use a 0–5 frequency scale (0 = *never*, 5 = *always*). The four theoretically proposed subscales are:

| Subscale | Code | Items | Example |
|---|---|:---:|---|
| Ascribed Submissiveness | AS | 9 | "Others have been surprised when I disagree with them." |
| Asian Fetishism | AF | 4 | "Others have treated me as if I am always open to sexual advances." |
| Media Invalidation | MI | 5 | "I rarely see AAW playing the lead role in the media." |
| Assumptions of Universal Appearance | AUA | 4 | "Others have suggested that all AAW look alike." |

---

## Methods

**Data simulation.** Data were simulated from the published factor loading matrix and item descriptives (N = 304, seed = 210927) using `MASS::mvrnorm(empirical = TRUE)`, reproducing the population covariance structure implied by Keum et al.'s (2018) published parameters.

**Models tested.**
- *Model 1 — Unidimensional:* All 22 items load on one general factor
- *Model 2 — First-Order Correlated Factors:* Items load exclusively on their designated subscale; all four factors permitted to correlate (oblique solution)

**Fit criteria.** χ² (exact fit), CFI ≥ .95 (incremental fit), RMSEA ≤ .05 (absolute fit, with 90% CI), SRMR < .10 (absolute fit). Nested model comparison via Δχ² and information criteria (AIC, BIC).

**Cross-platform replication.** Analysis conducted in R (`lavaan` v.0.6-9) and Python (`semopy` v.2.3); χ²(209) = 1004.14 (unidimensional) and χ²(203) = 220.86 (four-factor) replicated exactly across both platforms.

---

## Files in This Repository

| File | Description |
|---|---|
| `01_dfGRMSAAW.csv` | Dataset — 304 observations × 22 items, simulated from published parameters |
| `02_CFA_Analysis_R.Rmd` | R Markdown source — data simulation, CFA models, visualizations, APA write-up |
| `02_CFA_Analysis_R.md` | *(Knitted output)* Rendered analysis with tables and plots — **view this on GitHub** |
| `03_CFA_Analysis_Python.ipynb` | Python notebook — fully executed, renders with output on GitHub |
| `03_CFA_Analysis_Python.py` | Python source script — same analysis as the notebook |
| `04_Project_Report.md` | Full APA-style research report (abstract, method, results, discussion, references) |
| `fig1_correlation_heatmap.png` | Inter-item correlation matrix (items ordered by subscale) |
| `fig2_factor_loadings.png` | Factor loading bar chart — four-factor model |
| `fig3_model_comparison.png` | Side-by-side fit index and AIC/BIC comparison across models |

> **To view the R analysis with output:** click `02_CFA_Analysis_R.md` — GitHub renders it with all tables and plots. The `.Rmd` source file is included for full reproducibility.

---

## Analytical Skills Demonstrated

- Specifying and evaluating competing CFA models in `lavaan` (R) and `semopy` (Python)
- Data simulation from published psychometric parameters (`MASS::mvrnorm`, empirical moments)
- Multi-index fit evaluation: χ², CFI, TLI, RMSEA (with CI), SRMR
- Nested model comparison: Δχ² test, AIC, BIC
- Cross-platform replication (R ↔ Python) as a methodological accuracy check
- APA 7th-edition results write-up embedded directly in analysis documents
- Visualization: inter-item correlation heatmap, factor loading bar chart, model comparison chart

---

## References

Keum, B. T., Brady, J. L., Sharma, R., Lu, Y., Kim, Y. H., & Thai, C. J. (2018). Gendered racial microaggressions scale for Asian American women: Development and initial validation. *Journal of Counseling Psychology, 65*(5), 571–585. https://doi.org/10.1037/cou0000289

Kline, R. B. (2016). *Principles and practice of structural equation modeling* (4th ed.). Guilford Press.

Rosseel, Y. (2012). lavaan: An R package for structural equation modeling. *Journal of Statistical Software, 48*(2), 1–36. https://doi.org/10.18637/jss.v048.i02

Meshcheryakov, G., Igolkina, A., & Bikmukhametov, T. (2021). semopy: A Python package for structural equation modeling. *Journal of Statistical Software, 101*(1). https://doi.org/10.18637/jss.v101.i01
