# Structural Health Inequity During Pandemics
## A County-Level COVID-19 Mortality Analysis

**Live Report:** [View the Interactive Analysis](https://brianketchens.github.io/structural-health-inequity-covid/)

---

## Project Overview

This analysis examines county-level COVID-19 mortality across 2,904 
US counties from March 2020 through September 2022, with a focus on 
identifying the structural conditions that predicted which communities 
bore disproportionate and persistent pandemic burden.

The central finding challenges the dominant narrative of the pandemic 
response: after controlling for age structure, racial composition, 
poverty, and other covariates, the proportion of adults without a 
high school diploma was the strongest independent predictor of county 
COVID death rates (IRR = 85.5, 95% CI: 51.2-143.0, p<0.001). Black 
population share was not a statistically significant independent 
predictor (IRR = 0.958, p=0.425) after structural conditions were 
controlled for — indicating that the severe mortality disparities 
observed in majority Black communities reflect structural inequity 
rather than inherent demographic risk.

---

## Key Findings

**1. Excess Mortality Is Geographically Concentrated**
Just 14 counties (0.5%) reached extreme classification exceeding 
three standard deviations above the national mean. These counties 
are disproportionately small, rural, majority Black, and located 
in the Deep South — particularly Georgia, Mississippi, and Louisiana.

**2. Pandemic Burden Reorganized Completely After Wave 1**
Spearman rank correlation between Wave 1 and Delta county death 
rate rankings was effectively zero (ρ = -0.003). The communities 
that bore the greatest initial burden achieved relative protection 
by Delta through prior exposure immunity, while burden shifted to 
structurally disadvantaged rural communities with lower prior 
exposure and less healthcare infrastructure.

**3. Cases Became Less Lethal After Omicron**
The slope of the case rate to death rate relationship declined by 
85% between the pre-Omicron and Omicron/post-Omicron periods 
(0.0089 vs 0.0013), consistent with variant attenuation, 
accumulated population immunity, and changes in death attribution 
practices.

**4. Structural Conditions, Not Demographics, Predicted Persistent Burden**
157 counties remained in the top quartile of death rates across 
both Wave 1 and the Delta wave. These persistently high burden 
counties had nearly three times the national average Black 
population share (22.9% vs 8.4%), substantially higher poverty 
rates (19.5% vs 15.3%), and lower educational attainment (12.2% 
vs 8.9% without a high school diploma) — but were not 
distinguished by age structure (18.4% vs 18.9% age 65+).

**5. COVID Mortality Followed Consistent Winter Seasonality**
STL decomposition reveals a repeating annual seasonal component 
with winter peaks exceeding summer troughs by approximately 5 
deaths per 100k — a magnitude comparable to the underlying trend. 
Seasonality amplified existing structural disadvantage consistently 
across all three years of the analysis period.

---

## Methodology

| Component | Detail |
|-----------|--------|
| **Primary Data Source** | Google COVID-19 Open Data (covid19_open_data) |
| **Demographic Data** | US Census Bureau ACS 2019 5-Year Estimates |
| **Geographic Unit** | US County (FIPS code) |
| **Analysis Period** | March 2020 – September 2022 |
| **Counties Analyzed** | 2,904 of approximately 3,143 US counties (92%) |
| **ETL Platform** | Google BigQuery (SQL) |
| **Analysis Platform** | R Markdown (POSIT Cloud) |
| **Statistical Model** | Negative Binomial Regression |
| **Seasonal Analysis** | STL Decomposition via Loess |
| **Outlier Detection** | Funnel Plot with 95% and 99.8% Control Limits |

---

## Data Coverage Note

Six states have zero county-level coverage in the Google 
covid19_open_data pipeline (Alabama, Arkansas, Arizona, California, 
Colorado, and Connecticut). Demographic comparison of missing vs 
included counties indicates the coverage gap is less directionally 
biased than initially characterized — missing counties skew toward 
small rural white populations rather than the high-poverty majority 
minority communities driving the core findings. Core findings are 
assessed as robust to the current data gap. Complete national 
coverage is a Phase 2 priority.

The analytical data file (county_weekly.csv, 149MB) is excluded 
from this repository due to GitHub file size limits. It is 
generated from the BigQuery ETL documented in the R Markdown 
source file.

---

## Repository Structure
