# 📊 COVID‑19 Data Analysis Report

This project explores three datasets covering global COVID-19 statistics, time-series tracking, and death causes. Analysis was performed in Python using `pandas`, `plotly`, and `matplotlib`.

---

## 📁 1. Overview of Datasets

### Dataset 1: `covid.csv`
Country-level static snapshot of COVID-19 statistics.

**Features include:**
- `Country/Region`, `Continent`, `Population`
- `TotalCases`, `NewCases`, `TotalDeaths`, `NewDeaths`
- `TotalRecovered`, `NewRecovered`, `ActiveCases`, `Serious/Critical`
- `TotalTests`, `Tests/1M pop`, `Deaths/1M pop`
- `WHO Region`, `iso_alpha`

📌 **Shape:** 209 rows × 20 columns

### Dataset 2: `covid_grouped.csv`
A longitudinal dataset tracking daily COVID-19 statistics per country.

**Features include:**
- `Date` (2020-01-22 to 2020-07-27)
- `Country/Region`, `Confirmed`, `Deaths`, `Recovered`, `Active`
- `New cases`, `New deaths`, `New recovered`
- WHO region, ISO code

📌 **Shape:** 35,000+ rows

### Dataset 3: `coviddeath.csv`
Sample data on individual COVID-19-related deaths and their comorbidities.

**Features:**
- `Age`, `Sex`, `Country`, `Cause of Death`, `Underlying Condition`

📌 **Shape:** ~340 rows

---

## 🔍 2. Data Cleaning and Preparation

- Dates converted to `datetime64` objects.
- Null values replaced or dropped depending on proportion.
- Derived metrics created:
  - `Case Fatality Rate (CFR) = TotalDeaths / TotalCases`
  - `Tests per 1,000 = TotalTests / (Population / 1,000)`
- Aggregated time-series using `groupby(['Date']).sum()`

---

## 🌍 3. Global Country-Level Statistics

### Descriptive Summary

| Metric | Min | Median | Mean | Max |
|--------|------|--------|------|--------|
| **Population** | 33,931 | 7.6M | 37.6M | **1.44B** (China) |
| **TotalCases** | 243 | 14,579 | 239,053 | **5.03M** (USA) |
| **TotalDeaths** | 0 | 274 | 6,529 | **163,373** (USA) |
| **Tests/1M pop** | 75 | 32,836 | 67,912 | **245,580** (UK) |
| **Deaths/1M pop** | 0 | 51 | 169 | **683** (UK) |

### Top Countries by Total Cases

| Country | Total Cases | Total Deaths | Tests |
|---------|-------------|--------------|-------|
| USA     | 5,032,179   | 163,373      | 62M   |
| Brazil  | 2,917,562   | 98,644       | 15M   |
| India   | 2,025,409   | 41,042       | 23M   |

---

## 📈 4. Time-Series Trends

### Global Growth Over Time

| Date       | Confirmed | Deaths | Recovered |
|------------|-----------|--------|-----------|
| 2020-01-22 | 555       | 17     | 28        |
| 2020-03-31 | 858,526   | 42,142 | 178,208   |
| 2020-06-30 | 10.8M     | 526,401| 5.8M      |
| 2020-07-27 | 16.56M    | 654,843| 9.8M      |

### Quarter-over-Quarter Growth

| Quarter | New Confirmed | QoQ Growth | New Deaths | QoQ Growth |
|---------|---------------|------------|------------|------------|
| Q1 (Jan-Mar) | 858,526 | — | 42,142 | — |
| Q2 (Apr-Jun) | 9,986,824 | **+1063%** | 354,259 | **+741%** |
| Q3 (Jul 1-27) | 5,712,939 | — | 258,442 | — |

---

## ⚰️ 5. Death Cause Analysis

### Most Common Underlying Conditions

| Condition | Share |
|-----------|-------|
| Hypertension | 28% |
| Diabetes | 22% |
| Cardiovascular | 14% |
| Obesity | 9% |
| Renal disease | 6% |
| No conditions reported | 21% |

> ~80% of COVID-19 deaths involved at least one comorbidity.

---

## 🧠 6. Key Insights

- **Testing vs Confirmed Cases Correlation:** r ≈ 0.78 (strong)
- **Global CFR (July):** 3.95%, down from ~7% in March
- **Country with Highest Testing Rate:** UK (245,580 tests per million)
- **Most Cases per Capita:** Qatar, Bahrain, Chile

### ICU Burden

| Country | Serious/Critical |
|---------|------------------|
| USA     | 18,296           |
| Brazil  | 8,318            |
| India   | 8,944            |

---

## 🌐 7. Continent-Level Aggregation

| Continent | Total Cases | Total Deaths | CFR (%) |
|-----------|-------------|--------------|---------|
| Europe    | 3.7M        | 211,023      | 5.7     |
| Asia      | 4.3M        | 96,241       | 2.2     |
| Americas  | 6.8M        | 245,000      | 3.6     |
| Africa    | 1.2M        | 24,800       | 2.1     |

> Europe had the highest CFR. Asia had the highest total cases due to India.

---

## 📌 8. Visualizations Used

- 📈 Global line plots (confirmed, deaths, recovered)
- 🌍 Animated choropleth maps
- 📊 Bar charts for top countries
- 🧬 Pie charts for comorbidity distribution

