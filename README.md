# 🚦 Urban Mobility & Economic Productivity Analysis (2024)

![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical_Data_Vis-3776AB?style=for-the-badge)

## 📌 Executive Summary

### Context & Objective
This project evaluates the relationship between urban mobility metrics (traffic congestion, travel delays, and travel speed) and economic productivity (GDP per capita) across global metropolitan areas for the year 2024.

**Key Variables Analyzed:**
- `jams_delay` & `traffic_index_live`: Indicate traffic congestion severity and lost hours in traffic jams.
- `travel_time_live_per_10kms_mins`: Minutes required to travel 10 kilometers.
- `city_gdp_per_capita`: Reflects economic output per inhabitant (USD).

**Decision-Making Relevance:** High traffic congestion combined with low economic productivity signals reduced economic competitiveness, identifying key areas for urban infrastructure development and public transport investment.

---

## 🛠️ Data Pipeline & Methodology

1. **Data Cleaning & Standardization:**
   - Evolved raw column labels into standardized `snake_case` formats.
   - Converted temporal series (`UpdateTimeUTC`) to `datetime64` objects for accurate temporal aggregation, maintaining `year` as `int64` for seamless table relational joins.
   - Standardized string numerical fields (`population_m`, `city_gdp_per_capita`, `pm25`).

2. **Aggregation & Relational Integration:**
   - Grouped and calculated annual averages (`.mean()`) for core mobility metrics by `city`, `country`, and `year`.
   - Executed relational inner joins via `pd.merge(..., how='inner', on=['city', 'year'])` to retain strictly verified metropolitan records present in both traffic and economic datasets.

3. **Visual & Statistical Validation:**
   - **Boxplots (`jams_delay`):** Evaluated mean, median, and outlier distributions.
   - **Histograms (`city_gdp_per_capita`):** Analyzed metropolitan economic distribution.
   - **Dual-Axis Visualization:** Contrasted traffic delays against per capita productivity.

---

## 📊 Key Findings

- **Infrastructure Offset:** A higher GDP per capita does not strictly correlate with higher traffic congestion; developed economies frequently mitigate traffic density via robust public transit infrastructure.
- **Infrastructure Deficit:** Developing cities exhibit disproportionately high travel delays relative to their GDP output, indicating structural deficits in transit network capacity.

---

## 🎯 Strategic Recommendations

- **Priority Targets:** **Bogotá** and **Lima** represent urgent priorities for public policy intervention. Both display peak regional delay metrics (`jams_delay` and time per 10 km) paired with lower-middle `city_gdp_per_capita` ranges.
- **Productivity Disparity:** **Bogotá** exhibits the widest gap between hours lost in traffic and economic productivity, making it the primary candidate for targeted mass transit infrastructure investment.
- **Investment Allocation:** Direct development capital toward high-capacity public transport in "high congestion – low GDP" urban centers to unlock untapped economic productivity.

---

## 📁 Repository Structure

```text
├── notebooks/
│   └── urban_mobility_analysis.ipynb   # Complete analysis notebook with step-by-step code
├── reports/
│   └── urban_mobility_report.html      # Static interactive report export
└── README.md                           # Project documentation & summary
