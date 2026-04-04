# America's Broadband Problem — Executive Brief
**Dataset:** IMLS / BroadbandNow / FCC via Kaggle | **Analyst:** Mintay Misgano | **Year:** 2022

---

## The Business Problem

Before the COVID-19 pandemic, broadband access inequality across the U.S. was a persistent but largely invisible policy problem. The pandemic made it a national crisis: as schools, businesses, and government services moved online, millions of Americans in underserved counties found themselves without reliable home internet access. This project explores the scope of that gap — **which counties and states are most at risk of being left behind, and are communities with higher concentrations of Black Americans disproportionately impacted?**

---

## Approach

- Merged and cleaned three publicly available datasets: IMLS Indicators Workbook (ACS 5-year estimates + BroadbandNow commercial FCC data + BLS unemployment statistics), BroadbandNow Open Data, and Simple Maps county geodata — yielding **3,102 U.S. counties × 20 variables**
- Handled missing data rigorously: dropped negligible missings on the primary broadband cost variable, imputed five continuous variables at the column mean, and manually verified two county-level outliers (Kalawao County, HI and Rio Arriba County, NM) against trusted external sources
- Resolved a critical data quality issue: BroadbandNow's provider count (avg. 12 providers/county) was wildly inconsistent with FCC's national average of 4.1 — replaced with IMLS data
- Built a Tableau story with county- and state-level dashboards, geographic gradient analysis, and Black American population overlay via Tableau Map Layers

---

## Key Findings

- **The broadband gap is real and measurable.** County-level data reveals substantial variation in home broadband availability, speed, and cost — the "average" masks two very different Americas.
- **Poverty rate predicts broadband access better than government data.** The FCC's official broadband access metric wildly overestimates actual access because of how it operationalizes "available" — a single provider offering service in a census block counts the entire block as served, regardless of adoption or affordability.
- **Geographic gradients are clear.** Moving north, broadband availability, speed, and home usage increase. Moving east, broadband availability and cost increase — but so does the share of households lacking home computers and internet.
- **Coastal concentration creates a "Two Americas" pattern.** The vast majority of the U.S. population lives in small, coastal metropolitan counties. The vast majority of U.S. counties, however, are rural — and the two groups have dramatically different broadband outcomes.
- **Black American communities bear a disproportionate share of the gap.** Counties with the highest concentrations of Black Americans are disproportionately represented among those with the worst broadband outcomes — consistent with a disparate impact pattern.

---

## Recommendations

1. **Policymakers should stop using FCC data as the primary access metric.** It systematically overstates coverage. Microsoft's actual usage data and survey-based access measures (e.g., ACS home internet questions) provide a far more accurate picture of where the real access gap lies.
2. **Target infrastructure investment to high-poverty, rural, and majority-Black counties.** The data identifies which specific counties show the worst combinations of low access, high poverty, and concentrated minority populations — these should be first-in-line for infrastructure funding.
3. **Complement access with affordability interventions.** In many underserved counties, broadband is technically "available" but the cost-to-income ratio makes it inaccessible. Subsidy programs (e.g., ACP) need to be targeted to these specific geographies, not distributed uniformly.

---

## Impact

Identifying the specific counties most at risk — not just the national average — enables evidence-based targeting of infrastructure investment and subsidy programs. A county-level dashboard allows policymakers, advocacy organizations, and community planners to filter by state, poverty rate, and demographic composition and immediately identify where interventions will have the highest impact per dollar spent.

---

*Analysis by Mintay Misgano | Tools: Python, RapidMiner, Tableau | Data: 3,102 U.S. counties, IMLS/BroadbandNow/FCC/ACS, 2014–2020*
