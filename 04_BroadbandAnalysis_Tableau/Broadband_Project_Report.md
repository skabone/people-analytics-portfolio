# America's Broadband Problem
### A County-Level Analysis of Broadband Access, Equity, and Disparate Impact in the United States

**Author:** Mintay Misgano — Industrial-Organizational Psychology / People Analytics, Seattle Pacific University
**Tools:** Python · RapidMiner · Tableau
**Dataset:** IMLS / BroadbandNow / FCC / ACS / Simple Maps · N = 3,102 U.S. counties

---

## Abstract

Broadband access inequality in the United States represents one of the most consequential infrastructure equity challenges of the digital era. Using a merged county-level dataset of 3,102 U.S. counties (post-cleaning) drawn from the Institute of Museum and Library Services, BroadbandNow Open Data, and the FCC, this project examines the scope and geographic distribution of the broadband gap — and specifically whether Black American communities face disparate broadband outcomes. Data was cleaned in RapidMiner (replicated in the accompanying Python script), merged with Simple Maps geodata in Tableau, and visualized through a multi-dashboard Tableau story. Key findings: the broadband gap is real and substantial; poverty rate is a stronger predictor of broadband access than official FCC availability metrics; geographic gradients run north (better) to south (worse) and west (better) to east (mixed); and counties with the highest Black American population concentrations are disproportionately represented among those with the worst broadband outcomes.

---

## 1. Introduction and Business Problem

Even before the COVID-19 pandemic forced schools, workplaces, and government services online, broadband access across the United States was uneven. The pandemic transformed a persistent structural problem into a visible national crisis: students sat in school parking lots for Wi-Fi, remote work advantages accrued primarily to those in well-connected markets, and telehealth options were unavailable precisely where they were most needed.

This project began with a personal observation and a policy question: we know from decades of research that disparate impact — the differential effect of ostensibly neutral policies on protected groups — is not accidental. Resource distribution in the United States has historically concentrated infrastructure investment in affluent, predominantly white communities while underserving rural, low-income, and minority communities. Broadband access is not an exception to this pattern.

The project addresses two core research questions:

1. **Which U.S. counties and states are most at risk of being left behind in broadband access?**
2. **Are communities with higher concentrations of Black Americans disproportionately impacted — consistent with a disparate impact pattern?**

---

## 2. Data Description

### 2.1 Sources

The dataset integrates three primary sources blended prior to analysis:

**IMLS Indicators Workbook (primary):**
The Institute of Museum and Library Services compiled county-level broadband indicators from three sub-sources:
- U.S. Census Bureau American Community Survey (ACS), 5-year 2014–2018 estimates — providing demographic, economic, and technology-access variables
- BroadbandNow.com — a commercial aggregator of FCC data providing provider counts, costs, and availability metrics
- Bureau of Labor Statistics Local Area Unemployment Statistics

**BroadbandNow Open Data Challenge (supplementary):**
A publicly available dataset from BroadbandNow's open data initiative, hosted on GitHub, providing additional broadband metrics at the county level.

**Simple Maps U.S. Counties (geodata):**
Provides updated county-level population figures and latitude/longitude coordinates, joined to the primary dataset in Tableau via inner join to enable geographic mapping.

### 2.2 Variable Overview

| Domain | Variables |
|--------|-----------|
| Geography | County name, state, state abbreviation |
| Demographics | Population (2019 IMLS), Black American population (via Tableau Map Layers) |
| Economic | Unemployment rate (%), poverty rate (%), SNAP receipt rate (%), no health insurance (%) |
| Technology access | No home computer (%), no home internet (%), home broadband rate (%) |
| Broadband infrastructure | Number of providers (IMLS), broadband availability score, broadband cost |
| FCC/BBN metrics | Wired broadband (%), all speeds ≥25Mbps (%), avg download speed, access score, slow fraction |

### 2.3 A Critical Data Quality Issue

A key discovery during data exploration: the BroadbandNow provider count (`provide_bbn`) averaged 12 providers per county — nearly three times the FCC's reported national average of 4.1 providers per county. This discrepancy reflects a fundamental problem with how broadband "access" is operationalized in FCC data: a single provider offering service anywhere in a census block allows the FCC to count the entire census block as "served," regardless of whether households can actually subscribe, afford service, or achieve adequate speeds. The BroadbandNow commercial aggregation of this FCC data inherits and potentially amplifies this measurement problem. Where conflicting, IMLS-derived metrics were used in preference to BroadbandNow metrics.

---

## 3. Data Preparation

Data cleaning was performed in RapidMiner. The full process is replicated in the accompanying Python script (`Broadband_Data_Prep.py`).

### 3.1 Handling Missing Data

**Broadband Cost (40 missing, 1.3%):**
Two cost columns existed: `Price_BBN` (BroadbandNow, 111 missing) and `Broad_Cost_IMLS` (40 missing). The minimum, maximum, and mean of both columns were nearly identical, confirming they measured the same underlying quantity. The IMLS column was retained as the higher-quality source; the 40 rows with missing IMLS cost data were deleted (1.3% of records — negligible). `Price_BBN` was dropped entirely.

**Five continuous variables (13 total missing across all five):**
- `wired_bbn`, `all25_bbn`, `downave_bbn`, `access_bbn`, `slowfrac_bbn`
Missing values were replaced with column means. The proportion of missing cases was negligible (<0.5%), and the variables are continuous and roughly symmetric, making mean imputation appropriate.

**Unemployment Rate and Poverty Rate (1 missing each):**
Missing values were traced to specific counties and looked up from trusted external sources:
- Kalawao County, HI unemployment: 21% (DataUSA.io)
- Rio Arriba County, NM poverty rate: 24% (DataUSA.io)

### 3.2 Removing Redundant Columns

Three BroadbandNow columns were replaced by higher-quality IMLS equivalents and removed:
- `population_bbn` → replaced by `population_19` (IMLS): BBN population had more missing data and diverged from other sources
- `provide_bbn` → replaced by `broadProviders_num` (IMLS): BBN provider count (avg. 12) was implausibly high vs. FCC national average of 4.1
- `Lowestpricepermonth_bbn` → replaced by `broad_cost` (IMLS): same quantity, lower missingness

**Final dataset: 3,102 rows × 20 columns**

### 3.3 Tableau Join

Simple Maps county data (latitude, longitude, updated population) was joined to the cleaned dataset in Tableau using an inner join on county and state — a standard geographic enrichment step that preserves only counties present in both datasets.

---

## 4. Visualization Approach

The Tableau story was structured around four levels of analysis, with dashboards moving from national overview to county-level detail:

| Level | Dashboard |
|-------|-----------|
| National overview | State-level broadband access choropleth |
| County detail | County-level access map, color-scaled to national average |
| Geographic gradients | Latitude/longitude scatter-plot maps to reveal N/S and E/W patterns |
| Equity overlay | Black American population layer via Tableau Map Layers |

**Key design decision:** Color scales were centered on the national average rather than the data's minimum or maximum. This ensures the visualization conveys which counties are above or below baseline — a more meaningful reference than arbitrary scale endpoints, particularly given the extreme population outliers (e.g., Los Angeles County, CA with ~10 million residents in a dataset where the average county has ~120,000).

**State vs. county contrast:** Displaying both state-level and county-level data simultaneously revealed that state averages mask enormous within-state variation — a critical methodological point for policy targeting. High-population coastal metro areas "average up" their states while large numbers of rural counties in the same state remain significantly underserved.

---

## 5. Findings

### 5.1 The Broadband Gap Is Real

Substantial variation exists across counties in every broadband metric examined — home broadband rate, provider count, average download speed, and cost. This variation is not random: it correlates strongly with county-level poverty rates, population size, and geographic location. The "average American" broadband experience obscures two distinct realities.

### 5.2 Poverty Rate Predicts Access Better Than Government Data

Home broadband adoption rate (`home_havebroad%`) — a survey-based measure from the ACS — correlates more strongly with poverty rate than the FCC-derived broadband availability metric (`broad_avail`). This confirms what critics of FCC measurement methodology have argued: official "available" broadband statistics systematically overstate actual access by counting any provider presence in a census block as full coverage, without regard for affordability, adoption rates, or service quality.

### 5.3 Geographic Gradients

**North-South gradient:** As latitude increases (moving north), broadband availability, home broadband usage, average download speed, and home computer ownership all increase on average. Southern states — particularly rural areas of the Deep South — show the worst outcomes across multiple broadband metrics.

**East-West gradient:** Moving east, broadband availability and cost increase — but so does the proportion of households lacking home computers and home internet. The East Coast pattern reflects the combination of dense metro areas (high availability, high cost) and rural pockets (low availability). The West Coast shows high availability concentrated in metro areas with more severe rural gaps in between.

### 5.4 The Two Americas Pattern

The distribution of the U.S. population is highly concentrated: the vast majority of Americans live in a small number of high-density, coastal metro counties. The vast majority of U.S. counties, however, are rural with small populations. These two groups have dramatically different broadband outcomes. A national average computed without population weighting represents neither group accurately — it averages across a highly skewed distribution.

### 5.5 Disparate Impact on Black American Communities

Using Black American population data overlaid via Tableau Map Layers, counties with the highest concentrations of Black Americans are disproportionately represented among those with:
- The lowest home broadband rates
- The highest poverty rates (itself a broadband predictor)
- The fewest broadband providers
- The slowest average download speeds

This pattern is consistent with a disparate impact interpretation — that the neutral-appearing distribution of broadband infrastructure and pricing systematically disadvantages Black American communities at the county level.

---

## 6. Discussion

### 6.1 Policy Implications

**The FCC measurement problem requires urgent attention.** Policy designed around flawed access data will misallocate infrastructure investment. The finding that poverty rate predicts actual broadband adoption better than the official access metric suggests that demand-side interventions (subsidy programs targeting low-income households) may be as important as supply-side infrastructure expansion — and that both need to be informed by more accurate access data.

**County-level targeting outperforms state-level policy.** State-level broadband statistics routinely obscure dramatic within-state variation. Infrastructure investment programs designed at the state level will systematically miss the rural and minority communities most in need if they rely on state averages to allocate funds.

**Equity-centered broadband policy requires demographic data at the county level.** The overlay of Black American population concentration on broadband outcome maps makes the disparate impact pattern visible in a way that aggregate statistics do not. Policy design that ignores this geographic concentration will produce inequitable outcomes even if its stated goals are neutral.

### 6.2 Methodological Reflections

The decision to center color scales on the national average — rather than the data's own min/max — is a design choice with meaningful analytical consequences. In a dataset with extreme population outliers and a right-skewed outcome distribution, the national average is a more interpretable and policy-relevant reference point than data-driven scale endpoints. This principle generalizes to any geospatial visualization where the goal is to communicate above/below-baseline status rather than absolute magnitude.

The comparison of state vs. county level data revealed a general principle in public policy analytics: the unit of analysis matters enormously. Aggregating to the state level is politically convenient but analytically costly — it hides the variance that policy should be targeting.

### 6.3 Limitations

**Data vintage:** The IMLS data draws primarily from ACS 2014–2018 estimates. Broadband infrastructure has changed substantially since then, including the COVID-era surge in remote work and subsequent infrastructure investment. Current county-level outcomes may differ.

**FCC data quality:** As discussed, FCC-derived broadband availability metrics overstate actual access. This analysis uses IMLS data in preference where available, but the underlying FCC methodology problem affects the entire field.

**Demographic scope:** Due to data availability, the demographic analysis focused on Black American population concentration. A more complete equity analysis would include Hispanic/Latino, Native American, and rural white communities — all of whom face documented broadband access disparities.

**Causal inference:** All findings are associational. The correlation between Black American population concentration and poor broadband outcomes does not by itself establish causation or intent. A causal analysis would require historical infrastructure investment data, pricing data by provider and geography, and regulatory history.

---

## 8. Conclusion

This analysis provides county-level evidence that the U.S. broadband gap is real, geographically patterned, and inequitably distributed across racial and economic lines. The primary policy conclusion is straightforward: official broadband access metrics systematically overstate coverage; poverty rate is a better predictor of actual access; and the communities most at risk of being left behind are disproportionately rural, low-income, and majority-Black American.

The interactive Tableau story translates these findings into a navigable geographic tool — allowing policymakers, advocates, and community planners to move from national patterns to their specific counties in a few clicks. In the context of the Infrastructure Investment and Jobs Act and ongoing FCC measurement reform, county-level, equity-centered broadband analytics is not an academic exercise — it is the evidence base that infrastructure investment decisions should be built on.

---

## References

BroadbandNow. (2022). *BroadbandNow open data challenge dataset*. GitHub. https://github.com/BroadbandNow/Open-Data

Federal Communications Commission. (2021). *Fixed broadband deployment data*. FCC. https://www.fcc.gov/general/broadband-deployment-data

Institute of Museum and Library Services. (2020). *IMLS Indicators Workbook: Economic status and broadband availability and adoption*. IMLS. https://www.imls.gov

Microsoft. (2019). *Rural broadband data: Measuring broadband America*. Microsoft On the Issues. https://blogs.microsoft.com

Pew Research Center. (2021). *Home broadband adoption, computer ownership vary by race, ethnicity in the U.S.* Pew Research Center. https://www.pewresearch.org

Simple Maps. (2021). *US counties database.* Simple Maps. https://simplemaps.com/data/us-counties

U.S. Census Bureau. (2019). *American community survey 5-year estimates, 2014–2018.* U.S. Census Bureau. https://www.census.gov/programs-surveys/acs

---

*Analysis by Mintay Misgano | Tools: Python, RapidMiner, Tableau | Data: 3,102 U.S. counties, IMLS/BroadbandNow/FCC/ACS, 2014–2020*
