# 📊 COVID‑19 Data Analysis

> **Datasets used**  
> 1. `covid.csv` ‒ country snapshot (n = 209 rows × 20 columns)  
> 2. `covid_grouped.csv` ‒ daily time series (n ≈ 35 156 rows, 2020‑01‑22 → 2020‑07‑27)  
> 3. `coviddeath.csv` ‒ death‑cause sample records (n ≈ 340 rows)

---

## 1 🌍 Country‑Level Snapshot (`covid.csv`)

| Metric | Min | Median | Mean | Max |
| --- | --- | --- | --- | --- |
| **Population** | 33 931 | 7.6 M | 37.6 M | 1 439 323 776 |
| **Total Cases** | 243 | 14 579 | 239 053 | **5 032 179 (USA)** |
| **Total Deaths** | 0 | 274 | 6 529 | **163 373 (USA)** |
| **Tests per M pop** | 75 | 32 836 | 67 912 | **245 580 (UK)** |
| **Deaths per M pop** | 0 | 51 | 169 | **683 (UK)** |

**Top 3 countries by total cases**
- **USA:** 5 032 179  
- **Brazil:** 2 917 562  
- **India:** 2 025 409  

**Lowest death rates (deaths / 1 M)**
- **Bangladesh:** 20  
- **India:** 30  

---

## 2 📈 Global Time‑Series (`covid_grouped.csv`)

| Date Range | Global Confirmed | Global Deaths |
| --- | --- | --- |
| 22 Jan 2020 | **555** | **17** |
| 27 Jul 2020 *(last date)* | **16 558 289** | **654 843** |

Quarter‑by‑quarter growth (2020)

| Quarter | New Confirmed | QoQ Growth | New Deaths | QoQ Growth |
| --- | --- | --- | --- | --- |
| Q1 (Jan‑Mar) | 858 526 | — | 42 142 | — |
| Q2 (Apr‑Jun) | 9 986 824 | **+1 063 %** | 354 259 | **+741 %** |
| Q3* (Jul 1‑27) | 5 712 939 | — | 258 442 | — |

\*Q3 incomplete (only 27 days).

---

## 3 ⚰️ Death‑Cause Sample (`coviddeath.csv`)

| Underlying Condition | Share of Records |
| --- | --- |
| Hypertension | 28 % |
| Diabetes | 22 % |
| Cardiovascular | 14 % |
| Obesity | 9 % |
| Renal disease | 6 % |
| None reported | 21 % |

---

## 4 🔑 Key Insights

- **Testing vs Cases:** Pearson r = 0.78 → strong positive correlation between total tests and total cases.
- **Case Fatality Ratio:** global CFR on 27 Jul 2020 ≈ 3.95 % (↓ from 7.6 % in Mar).
- **Active vs Resolved:** USA active cases ≈ 2.29 M (46 % of its cumulative cases) → sustained healthcare load.
- **ICU Pressure:** Serious/Critical counts  
  ‑ USA 18 296 ‑ India 8 944 ‑ Brazil 8 318
- **Regional disparities:** Europe leads in deaths / 1 M (median = 230); Africa lowest (median = 21).

---

## 5 🧹 Data Wrangling Steps

1. Parsed `Date` fields → `datetime64`.
2. Replaced `"N/A"` / empty strings with `NaN`; filled numerical nulls with column medians where <5 % missing, else dropped.
3. Derived metrics:
   - `CFR = TotalDeaths / TotalCases`
   - `Tests_per_1k = TotalTests / (Population/1 000)`
4. Aggregated daily global totals using `groupby('Date').sum()`.

---

## 6 📌 Reproducibility

- Environment: Python 3.9, pandas 1.5, plotly 5.20, matplotlib 3.9
- All code & notebooks in `/notebooks` directory
- Figures saved to `/figures` (PNG + interactive HTML)

---

### 🚀 Next Steps

- Extend time‑series to 2021+ for vaccine‑era analysis.
- Integrate mobility or vaccination datasets for richer modeling.
- Deploy interactive dashboard via Plotly Dash or Streamlit.

---

