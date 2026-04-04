# Project 10 — Employee Engagement Survey Design

**End-to-end survey design** | UWES-grounded | Quarterly pulse format | Connected to psychometric validation (Project 05)

---

## Overview

A complete survey design specification for a quarterly Employee Engagement Pulse Survey, grounded in the Utrecht Work Engagement Scale (Schaufeli et al., 2002). This project covers every stage of the survey lifecycle — business case, research design, theoretical framework, item development, sampling strategy, administration protocols, scoring, and analysis planning — and connects the design to the psychometric validation workflow demonstrated in Project 05.

---

## Instrument Summary

| Feature | Specification |
|:--------|:-------------|
| Framework | Utrecht Work Engagement Scale (UWES-15) |
| Dimensions | Vigor (5 items), Dedication (5 items), Absorption (5 items) |
| Total items | 20 (15 engagement + 5 demographic) |
| Response scale | 5-point Likert (Strongly Disagree → Strongly Agree) |
| Administration | Quarterly / Qualtrics anonymous link |
| Completion time | 10–15 minutes |
| Sampling | Stratified random (by department), n ≥ 30 per stratum |

---

## Key Design Choices

- **Pulse over comprehensive:** 20 items quarterly → higher response rates + faster insight cycles
- **Subscale scoring over composite:** Vigor, Dedication, and Absorption reported separately → targeted interventions
- **Demographics at the end:** Reduces stereotype threat effects on engagement items
- **Full anonymization:** Maximum honest responding; no respondent-ID linkage

---

## Validation Pathway

```
Pilot Study (n ≥ 100)
  ↓
Reliability: α ≥ .75 per subscale; item r.drop ≥ .40
  ↓
EFA: 3-factor PAF (oblique); loadings ≥ .50, cross-loadings < .30
  ↓
CFA: CFI ≥ .95, RMSEA ≤ .06
  ↓
Production Deployment → Quarterly HRIS Linkage → Attrition Prediction
```

See [Project 05](../../05_Psychometrics_Scale_Validation_R/) for the full psychometric validation workflow.

---

## Files

| File | Description |
|:-----|:------------|
| `Employee_Engagement_Survey_Design.md` | Complete design spec: business case, instrument, sampling, scoring, analysis plan, references |
| `Executive_Brief.md` | 1-page practitioner summary |
| `README.md` | This file |

---

## Tools & References

- **Design framework:** UWES-15 (Schaufeli, Salanova, González-Romá, & Bakker, 2002)
- **Sampling methodology:** Stratified random sampling (Sudman et al., 1996)
- **Administration platform:** Qualtrics
- **Validation workflow:** psych package (R) — see Project 05

---

*Part of the [People Analytics Portfolio](../README.md) | Analyst: Mintay Misgano | Course: Survey Design and Development, SPU (Summer 2023)*
