# 🌍 COVID‑19 Data Analysis Project

## Description
This project involves the analysis of global COVID‑19 pandemic data using three distinct datasets. The goal is to uncover insights into the virus's spread, testing efforts, mortality, and underlying comorbidities across different countries and regions. The analysis combines time-series trends, static country-level snapshots, and health condition data to support public health understanding and decision-making.

**Data Sources**: Publicly available datasets including global time series, U.S. mortality reports, and current global country statistics.

---

## Objectives

The main goals of this project are to:

- **Track the Spread of COVID‑19**  
  Monitor global case, death, and recovery trends from January to July 2020.

- **Evaluate Testing Efficacy**  
  Explore the relationship between testing rates and confirmed case counts using correlation analysis.

- **Identify High-Risk Populations**  
  Analyze comorbidities among U.S. COVID-related deaths to determine vulnerable health conditions.

- **Compare Country and Continent Responses**  
  Examine disparities in outcomes across nations and regions using per-capita metrics.

- **Enhance Technical Capabilities**  
  Improve data engineering, time series aggregation, and dashboard storytelling skills using Python and Power BI.

---

## Project Phases

### 🧹 Data Preparation

#### Data Examination
Three datasets were reviewed for structure and granularity:

| File               | Granularity         | Key Fields                                                                 |
|--------------------|---------------------|-----------------------------------------------------------------------------|
| `covid.csv`        | Static (Global)     | Country, Population, Total Cases, Deaths, Tests, WHO Region, iso_alpha     |
| `covid_grouped.csv`| Daily Time Series   | Date, Country, Confirmed, Deaths, Recovered, WHO Region                    |
| `coviddeath.csv`   | Weekly (US-Only)    | Age Group, State, Condition, COVID Deaths, ICD-10 Codes                    |

#### Data Transformation
- Column names standardized to `snake_case`
- Dates converted to `datetime64[ns]`, numerics to `int64/float64`
- Created surrogate keys for `us_state_id` and ISO Alpha-3 codes
- Derived new fields:
  - `epi_week` from `start_week`
  - `case_fatality_ratio = total_deaths / total_cases`
- Handled missing values using forward-fill for time series, retained NaNs for future dates
- Output saved in `.parquet` format
- Final schema modeled in a star-schema format:
  - Dimensions: `dim_country`, `dim_state`
  - Facts: `fact_covid_daily`, `fact_covid_weekly`

---

### 📊 Data Analysis

#### Key Focus Areas

- **Global Case Trends**
  - COVID-19 grew from 555 cases (Jan 22) to 16.56M (Jul 27)
  - CFR dropped from ~7% in March to **3.95% in July**

- **Top Countries by Total Cases**
  | Country | Total Cases | Total Deaths | Tests Conducted |
  |---------|--------------|----------------|------------------|
  | USA     | 5,032,179    | 163,373        | 62M              |
  | Brazil  | 2,917,562    | 98,644         | 15M              |
  | India   | 2,025,409    | 41,042         | 23M              |

- **Quarterly Growth**
  | Quarter     | New Confirmed | QoQ Growth | New Deaths | QoQ Growth |
  |-------------|----------------|-------------|--------------|--------------|
  | Q1 (Jan–Mar) | 858,526        | —           | 42,142       | —           |
  | Q2 (Apr–Jun) | 9,986,824      | +1,063%     | 354,259      | +741%       |
  | Q3 (Jul 1–27)| 5,712,939      | —           | 258,442      | —           |

- **Comorbidity Analysis (U.S. Deaths)**
  - Hypertension: 28%
  - Diabetes: 22%
  - Cardiovascular Disease: 14%
  - ~80% of deaths had ≥1 underlying condition

- **Testing vs. Case Detection**
  - Pearson correlation (r ≈ 0.78) between tests per 1K and confirmed cases
  - UK had the highest testing rate: 245,580 tests per million

- **Continent-Level Breakdown**
  | Continent | Total Cases | Total Deaths | CFR (%) |
  |-----------|-------------|--------------|---------|
  | Europe    | 3.7M        | 211,023      | 5.7     |
  | Asia      | 4.3M        | 96,241       | 2.2     |
  | Americas  | 6.8M        | 245,000      | 3.6     |
  | Africa    | 1.2M        | 24,800       | 2.1     |

---

### 📑 Report Creation

#### Insights Presentation
The final report was designed in Power BI with the following key pages:

- **Overview Dashboard**  
  Global KPIs, top countries, animated case maps

- **Time Series Trends**  
  7-day moving averages, cumulative growth, Q/Q comparison

- **Country Deep-Dives**  
  Drill-down into country testing vs. outcomes, ICU load

- **Testing & Correlation**  
  Scatter plots of tests vs. confirmed cases, outlier detection

- **Comorbidity Panel**  
  Pie charts and stacked bars of U.S. death causes by age group

- **Continent Comparison**  
  CFR, deaths per million, and normalized case comparisons

- **Data Quality & Validation**  
  Missing value coverage, type checks, iso_alpha matching

📎 **Link to the Interactive Power BI Report**: *Report*

> ⚠️ **Disclaimer**: This report uses EN-US regional settings and may need adjustment for other locales.

---

## 🎯 Actionable Insights

- Countries with high testing rates have significantly higher case detection — underreporting is likely in under-tested regions.
- The global decline in CFR suggests improved treatment and broader detection of mild cases.
- ICU pressures are concentrated in countries with high active and serious/critical cases — resource allocation should prioritize these zones.
- Nations with high comorbidity burdens (e.g., hypertension, diabetes) need targeted health interventions and vaccination strategies.
- Europe had the highest CFR despite fewer per capita cases — healthcare system response and demographics may be influencing outcomes.

---
