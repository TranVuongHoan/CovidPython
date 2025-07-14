# COVID‑19 Insight Dashboard Report

## Insights Presentation
The report is structured in interactive pages, each targeting a critical aspect of the pandemic. All pages support **global filters** for **Date (rolling, monthly, quarterly)** and **Country/Continent/WHO Region**, enabling tailored exploration of trends.

**Link to the Interactive Power BI Report:** *Report*

> **Disclaimer:** Figures reflect the data snapshot ending **2020‑07‑27** (for the time series) and **latest available totals** (for the static snapshot). Units follow **EN‑US** formatting; adjust your regional settings if required.

---

## Overview
| Element | Purpose |
|---------|---------|
| **Global KPIs** – Confirmed, Deaths, Recovered, CFR, Tests per 1K | Immediate view of pandemic scale and lethality |
| **Weekly/Monthly Trend Lines** – Confirmed vs Deaths | Gauge trajectory and lag between cases & fatalities |
| **Top 10 Countries by Confirmed & Deaths** (bar) | Identify current epicentres |
| **Continental Share (100 % stacked bar)** | Compare cross‑continent burdens |
| **Cumulative Map (choropleth)** | Visualise geographic spread |

---

## Time‑Series Trends
| Element | Purpose |
|---------|---------|
| **Growth Curves** (log & linear) | Show acceleration/plateau phases |
| **Quarter‑over‑Quarter Δ** table | Highlight surge periods (e.g., **+1 063 % Q2 2020**) |
| **7‑Day MA New Cases/Deaths** | Smooth short‑term volatility |
| **Forecast Panel** (ETS/ARIMA optional) | Short‑range projections & confidence bands |

---

## Country Deep‑Dive
| Element | Purpose |
|---------|---------|
| **Country Selector** | Drill down to individual nations |
| **Daily Cases vs Tests** (dual axis) | Assess testing adequacy |
| **Hospital Stress** – Active & Serious/Critical beds | Flag ICU capacity issues |
| **Policy Timeline Strip** (lockdowns, travel bans) | Contextualise inflection points |
| **Case Fatality Rate Trend** | Monitor medical outcome improvements |

---

## Testing vs Outcomes
| Element | Purpose |
|---------|---------|
| **Scatter: Tests per 1K vs Confirmed per 1K** | Reveal under‑/over‑testing regions |
| **Correlation Card (r ≈ 0.78)** | Quantify strength of association |
| **Quadrant Analysis** – High Tests / Low Cases etc. | Target for policy benchmarking |

---

## Death Comorbidity Analysis (US Sample)
| Element | Purpose |
|---------|---------|
| **Comorbidity Pie / Bar** | Hypertension (28 %), Diabetes (22 %), etc. |
| **Stacked Bar by Age Group** | Show shifting risk profiles |
| **Underlying vs Principal Cause Matrix** | Clarify coding nuances |

---

## Continent Comparison
| Element | Purpose |
|---------|---------|
| **Totals & CFR Table** | Europe CFR 5.7 %, Asia highest cases |
| **Heat Map** – Cases & Deaths per 1M | Normalised burden |
| **Trend Small‑Multiples** | Parallel curves for each continent |

---

## Data Quality & Definitions
| Element | Purpose |
|---------|---------|
| **Dataset Lineage Diagram** | From raw `.csv` ➜ transformed `.parquet` |
| **Field Glossary** | Clarify iso_alpha, epi_week, CFR formula |
| **Missing Data Coverage Table** | Highlight NaN treatment decisions |
| **Validation Checks** (icons) | ✔ iso_alpha alignment, ✔ state‑to‑US death sums |

---

## Actionable Insights
- **Testing intensity strongly linked to detected cases (r ≈ 0.78)** → nations below trendline likely under‑detecting.
- **Global CFR fell from ~7 % (Mar 2020) to 3.95 % (Jul 2020)** → treatment improvements & broader testing.
- **Europe’s CFR (5.7 %) > global mean** despite lower per‑capita cases → investigate demographic & health‑system factors.
- **ICU hotspots** – USA, Brazil, India hold highest Serious/Critical counts; capacity planning imperative.
- **Four in five recorded COVID‑19 deaths include ≥1 comorbidity** → prioritise chronic‑disease management in mitigation strategies.

---

