# 🦠 COVID‑19 Insight Dashboard Report

## 📊 Insights Presentation

This report presents an interactive and comprehensive analysis of the global COVID‑19 pandemic, leveraging three datasets that offer diverse granularity: a country-level static snapshot, a daily time-series, and a U.S.-specific death cause breakdown. The data was transformed and modeled into a star schema to facilitate fast querying and dashboard visualization.

👉 **Link to Interactive Power BI Report**: *Report*  
🗓️ **Reporting Period**: January 22, 2020 – July 27, 2020  
🌍 **Geographic Scope**: Global + U.S. Death Data  
🧪 **Tools Used**: Python (Pandas, Plotly, Matplotlib), Power BI  

> ⚠️ **Disclaimer**: All figures follow EN‑US locale (e.g., decimal points, comma separators). Regional settings may affect display units. Use filters for custom date ranges, countries, or WHO regions.

---

## 🧷 Overview Page

Provides a high-level view of global pandemic conditions, updated weekly and monthly.

### Key Visuals & Metrics:
- **Global Summary KPIs**:  
  - Total Confirmed Cases  
  - Total Deaths  
  - Case Fatality Ratio (CFR = deaths / cases)  
  - Total Recovered  
  - Testing Rate per 1,000 people  
- **Trend Lines**:  
  - Confirmed vs. Deaths (cumulative and new cases)  
  - 7-day Moving Averages for smoother trend interpretation  
- **Geospatial Distribution**:  
  - **Animated Choropleth Map**: Spatiotemporal growth visualization  
  - **Bar Charts**: Top 10 countries by cases, deaths, testing  
  - **Stacked Bar (100%)**: Share of cases & deaths by continent

### Purpose:
- Identify regions with rising case volumes
- Track daily and cumulative pandemic evolution
- Understand global and regional response disparities

---

## 📈 Time-Series Trends Page

Analyzes the longitudinal dataset `covid_grouped.csv` with over 35,000 daily records.

### Components:
- **Global Growth Timeline**:
  - Jan 22: 555 cases → July 27: 16.56M confirmed  
  - Deaths rose from 17 → 654,843  
  - Recoveries: 28 → 9.8M
- **Quarterly Growth Table**:
  | Quarter     | New Confirmed | QoQ Growth | New Deaths | QoQ Growth |
  |-------------|----------------|-------------|--------------|--------------|
  | Q1 (Jan–Mar) | 858,526        | —           | 42,142       | —           |
  | Q2 (Apr–Jun) | 9,986,824      | +1,063%     | 354,259      | +741%       |
  | Q3 (Jul 1–27)| 5,712,939      | —           | 258,442      | —           |
- **Moving Averages**: For smoothing volatility in new cases & deaths
- **Log vs Linear Scale Toggle**: To accommodate exponential growth visualization

### Purpose:
- Track turning points and acceleration/deceleration phases
- Compare growth dynamics between quarters
- Use forecast models to estimate short-term future cases

---

## 🌍 Country Deep-Dive Page

Analyzes data from `covid.csv` — a static global snapshot with ~209 countries.

### Key Visuals:
- **Country Selector**: Filters all visuals by selected country
- **Testing vs. Cases Trend**: Tests conducted alongside confirmed cases
- **Serious/Critical Case Counts**: Indicates ICU burden
- **Population-Normalized Metrics**:
  - Cases per Million
  - Deaths per Million
  - Tests per Million

### Top Countries (as of July 27):
| Country | Total Cases | Total Deaths | Total Tests |
|---------|--------------|----------------|----------------|
| USA     | 5,032,179    | 163,373        | 62,000,000     |
| Brazil  | 2,917,562    | 98,644         | 15,000,000     |
| India   | 2,025,409    | 41,042         | 23,000,000     |

### Purpose:
- Understand country-specific burden & response
- Support comparative policy evaluation
- Benchmark high- and low-performing countries

---

## 🧪 Testing vs. Outcomes Correlation Page

Explores the relationship between testing rates and confirmed case rates.

### Visuals & Stats:
- **Scatter Plot**:
  - X: Tests per 1,000 people
  - Y: Confirmed cases per 1,000 people
  - Highlight outliers (e.g., UK high testing with moderate cases)
- **Correlation Coefficient**:  
  - Pearson’s r ≈ **0.78** → strong positive relationship
- **Quadrant Chart**:  
  - High Testing / High Cases → extensive outbreaks  
  - High Testing / Low Cases → effective containment  
  - Low Testing / High Cases → underreporting risk  
  - Low Testing / Low Cases → low risk or lack of detection

### Purpose:
- Validate testing effectiveness
- Identify underreported regions
- Guide test deployment strategy

---

## ⚰️ Comorbidity Analysis (U.S. Deaths) Page

Derived from `coviddeath.csv` — granular data on comorbidities in U.S. COVID‑19 deaths.

### Findings:
- **Top Comorbidities**:
  - Hypertension: 28%
  - Diabetes: 22%
  - Cardiovascular: 14%
  - Obesity: 9%
  - Renal Disease: 6%
  - No Conditions: 21%
- **Age-wise Distribution**: Older age groups showed higher comorbidity load
- **Underlying vs. Principal Cause Matrix**: Clarifies cause attribution

### Purpose:
- Support clinical risk profiling
- Inform healthcare policy for vulnerable populations
- Drive public messaging on comorbidity risk

---

## 🌐 Continent-Level Comparison Page

Aggregates case and fatality statistics by continent.

### Summary Table:
| Continent | Total Cases | Total Deaths | CFR (%) |
|-----------|-------------|--------------|---------|
| Europe    | 3.7M        | 211,023      | 5.7     |
| Asia      | 4.3M        | 96,241       | 2.2     |
| Americas  | 6.8M        | 245,000      | 3.6     |
| Africa    | 1.2M        | 24,800       | 2.1     |

- **Small Multiples**: Parallel trend charts per continent
- **CFR Bar Chart**: Europe highest; Asia lowest
- **Per Capita Analysis**: Normalize by population

### Purpose:
- Analyze intercontinental disparities
- Support resource prioritization
- Understand geography-driven trends

---

## 📁 Data Lineage & Engineering Page

### Source Files:
- `covid.csv`: Static snapshot (209 countries)
- `covid_grouped.csv`: Daily time series (Jan–Jul 2020)
- `coviddeath.csv`: U.S. death data (weekly)

### Engineering Highlights:
- **Column Renaming**: snake_case standardization
- **Type Conversion**:
  - Dates → `datetime64[ns]`
  - Numerics → `float64`/`int64`
- **New Features**:
  - `epi_week` (from `start_week`)
  - `case_fatality_ratio = total_deaths / total_cases`
- **Surrogate Keys**:
  - `us_state_id` mapping
  - Country → ISO Alpha-3
- **Missing Value Treatment**:
  - Forward-fill for time series continuity
  - Preserve future weeks as NaN for forecasting
- **Saved as `.parquet`** for optimized performance
- **Star Schema Structure**:
  - `dim_country`, `dim_state`
  - `fact_covid_daily`, `fact_covid_weekly`

---

## 🧠 Key Insights Summary Page

- **CFR Decline**: From ~7% (Mar 2020) → **3.95% (Jul 2020)** due to better treatment/testing.
- **Underreporting Risks**: Low testing countries with high CFRs (e.g., parts of Africa).
- **UK Leads Testing**: 245,580 tests per million people.
- **Highest Per Capita Cases**: Qatar, Bahrain, Chile.
- **ICU Pressure Points**:
  | Country | Serious/Critical |
  |---------|------------------|
  | USA     | 18,296           |
  | India   | 8,944            |
  | Brazil  | 8,318            |
- **Comorbid Conditions**: >80% of COVID deaths involved at least one underlying issue.

---

## 📊 Visual Types Used

- **Line Charts**: Cumulative & daily global case trends
- **Animated Choropleth Maps**: Spatiotemporal spread
- **Bar & Stacked Charts**: Top countries, continents
- **Pie Charts**: Comorbidity proportions
- **Scatter Plots**: Testing vs outcome correlation
- **Tables & Cards**: Summarized KPIs and growth metrics
- **Heatmaps & Matrix Charts**: CFR and comorbidity breakdowns
