# Confirmatory Factor Analysis: GRMSAAW Scale Validation
**Executive Brief** | People Analytics | Measurement & Survey Research

**Analyst:** Mintay Misgano | **Tools:** R (lavaan), Python (semopy) | **Sample:** N = 304

---

## The Business Problem

Organizations that use employee surveys to capture experiences of discrimination, microaggressions, or belonging must be confident their instruments are actually measuring what they claim to measure. A survey built on shaky psychometric foundations produces misleading data — and misleading data leads to misdirected DEI interventions.

This project asks a specific and practically important question: does the Gendered Racial Microaggressions Scale for Asian American Women (GRMSAAW) function as a single general measure of microaggression exposure, or does it capture four meaningfully distinct dimensions? The answer determines how the instrument should be scored, reported, and acted on.

---

## The Approach

Using **Confirmatory Factor Analysis (CFA)** — the gold-standard technique for validating pre-specified measurement structures — I tested two competing models against the same data (N = 304):

- **Model 1 (Unidimensional):** All 22 items reflect a single latent construct
- **Model 2 (Four-Factor Correlated):** Items load on four subscales — Ascribed Submissiveness (9 items), Asian Fetishism (4 items), Media Invalidation (5 items), and Assumptions of Universal Appearance (4 items) — which are permitted to correlate

Fit was evaluated on five complementary indices (χ², CFI, RMSEA, SRMR, AIC/BIC), and models were formally compared using a chi-square difference test.

Analysis was conducted in both **R** (lavaan package) and **Python** (semopy), confirming identical χ² results across platforms.

---

## Key Findings

The four-factor model is dramatically superior to the single-factor model on every criterion:

| Fit Index | Model 1 (Unidimensional) | Model 2 (4-Factor) | Benchmark |
|---|:---:|:---:|---|
| CFI | .578 | **.991** | ≥ .95 acceptable |
| RMSEA | .112 | **.017** [.000, .031] | ≤ .05 good |
| SRMR | .124 | **.058** | < .10 acceptable |
| AIC | 17,755 | **16,984** | lower = better |
| BIC | 17,919 | **17,170** | lower = better |
| Δχ²(6) | — | **783.28, p < .001** | significant = better model |

All 22 item loadings on the four-factor model are statistically significant, with standardized loadings ranging from .35 (MI5) to .82 (AUA1). The four subscales are mildly correlated with each other (all r < .10), confirming they are distinct but related constructs.

---

## Recommendations

1. **Score and report subscales separately.** The data confirm four distinct dimensions, not one. A single composite "microaggression score" would obscure meaningful variation. HR analytics teams should track Ascribed Submissiveness, Asian Fetishism, Media Invalidation, and Universal Appearance independently.

2. **Use this framework as a template for DEI survey validation.** Any time a new or adapted survey instrument is deployed, a quick CFA (3–5 hours of analyst time) should confirm the intended structure holds in your specific workforce before results are acted on.

3. **Design targeted interventions by subscale.** Different subscales likely require different organizational responses — Media Invalidation may call for representation-focused communications, while Ascribed Submissiveness may point to leadership pipeline and advocacy training.

---

## Why This Matters for People Analytics

Measurement quality is the foundation of people analytics. An unvalidated survey produces noise. A validated one produces signal. CFA is how you tell the difference — and it's a skill set that belongs in any rigorous people analytics function alongside regression, ML, and dashboarding.

This project demonstrates the full validation workflow: instrument theory → data simulation from published loadings → competing model specification → fit evaluation → formal model comparison → APA-quality write-up — replicable in both R and Python.
