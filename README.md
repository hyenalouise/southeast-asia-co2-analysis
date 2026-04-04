# Southeast Asia CO₂ Analysis: Indonesia as the Pivot Point

> **An end-to-end environmental data analytics project** from raw global emissions data to policy recommendations, demonstrating data quality assurance, trend analysis, emissions decomposition, and forecasting.



## Project Overview

Indonesia is not Southeast Asia's highest per-capita CO₂ emitter, but it is the region's largest **absolute** driver of emissions, due to scale, rapid economic growth, and deep coal dependency.

This project analyses Indonesia's historical CO₂ emissions (1889–2023), decomposes the structural drivers of growth, applies a 5-year forecast, and recommends data-backed energy policy interventions. It was originally presented as a bootcamp capstone (Sprint 1) and has since been extended with a reproducible Python QA pipeline.



## Key Findings

| Finding | Value |
|---|---|
| Peak CO₂ emissions (2022) | **737.07 Mt** |
| Total growth 2000–2022 | **+162%** (281 Mt → 737 Mt) |
| Dominant driver of growth | GDP per capita (Affluence Effect: +411 Mt) |
| Energy intensity savings (2000–2013) | −120 Mt (efficiency was working) |
| Coal effect after 2015 coal push | +45 Mt (efficiency gains reversed) |
| 5-year forecast (2028) | **831.40 Mt** (+14%) |
| Recommended CO₂ reduction potential | −30.65 Mt/year via nuclear + geothermal |



## Repository Structure

```
southeast-asia-co2-analysis/
│
├── data/
│   └── owid-co2-raw.csv             ← Raw dataset (Our World in Data)
│
├── outputs/
│   ├── indonesia-co2-cleaned.csv    ← Cleaned Indonesia dataset (135 rows × 25 cols)
│
├── notebooks/
│   ├── indonesia-co2-eda.ipynb      ← Exploratory analysis (coming soon)
│   └── owid_co2_datacleaning.ipynb  ← Python QA & cleaning script
│
└── README.md
```



## Data Source

**Dataset:** Our World in Data — CO₂ and Greenhouse Gas Emissions  
**Coverage:** 255 countries and regions, 1750–2023, 79 variables  
**Rows:** 50,191 | **Columns:** 79  
**Link:** [ourworldindata.org/co2-and-greenhouse-gas-emissions](https://ourworldindata.org/co2-and-greenhouse-gas-emissions)



## QA & Data Cleaning Process

The raw dataset required significant quality assessment before analysis. All steps are documented and reproducible.

### Run the pipeline

```bash
pip install pandas numpy
python qa_pipeline.py
```

### QA checks performed

| # | Check | Finding | Action |
|---|---|---|---|
| QA-01 | Schema validation | All 12 required columns present | None |
| QA-02 | Global completeness | gdp: 69.6% null; coal_co2: 56.7% null | Documented — gaps in historical records |
| QA-03 | Duplicate records | 0 duplicate country-year pairs | None |
| QA-04 | Aggregated regions | 7,929 rows are regional totals (e.g. "Asia", "World") | Excluded from country-level analysis |
| QA-05 | Negative CO₂ values | None found across all fuel types | None — range check passed |
| QA-06 | YoY growth outliers | 117 records with \|growth\| > 500% | Flagged; valid for early industrialisation |
| QA-07 | Indonesia completeness | 22.4% nulls in CO₂ columns (1850–1888 only) | Analysis scoped to 1889–2023 |
| QA-07c | Indonesia modern data | 0 nulls in 2000–2023 | All modern records complete |

**Result:** 0 critical issues. Cleaned dataset: **135 rows × 25 columns** (Indonesia, 1889–2023).



## Analysis Highlights

### 1. Structural upward shift, not temporary
Indonesia's emissions remained low and stable through most of the 20th century, then accelerated sharply in the 21st century, reaching a record **737 Mt in 2022**.

### 2. The Coal Trap (post-2014)
Before 2014, Indonesia was decoupling growth from emissions — efficiency improvements saved **120 Mt** between 2000–2013. After the 2015 "35,000 Megawatt" coal power expansion, the grid became **dirtier** (+45 Mt from carbon intensity) and efficiency gains stalled.

### 3. Kaya Identity decomposition (2000–2022)
Using a waterfall decomposition of the Kaya Identity:

| Driver | CO₂ contribution |
|---|---|
| Affluence Effect (GDP per capita) | +411 Mt |
| Population Effect | +121 Mt |
| Carbon Intensity Effect | +42 Mt |
| Energy Intensity Effect | −117 Mt |
| **Total change** | **+456 Mt** |

### 4. Forecast
A 5-year projection using trend regression places Indonesia at **831 Mt by 2028** (+14%), with continued coal dependency and industrial growth as key upside risks.



## Recommendations

Based on the analysis, two energy source categories offer the best balance of low CO₂ emissions and high energy density per land area:

| Energy Source | Land needed | Added supply | CO₂ saved/year |
|---|---|---|---|
| Nuclear | 1.5 km² | 3 GW | 23.64 Mt |
| Geothermal | 8 km² | 1 GW | 7.01 Mt |
| **Total** | **9.5 km²** | **4 GW** | **30.65 Mt** |

A sustained 5% annual emissions reduction via clean energy transition could bring Indonesia from ~750 Mt (2026) to below 300 Mt by 2040.



## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Power Query](https://img.shields.io/badge/Power_Query-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)



## Skills Demonstrated

- Environmental data QA and quality control (completeness, range, outlier, duplicate checks)
- Emissions decomposition (Kaya Identity / waterfall analysis)
- Time series trend analysis and forecasting
- Policy-driven data storytelling
- Reproducible, documented data pipelines
- Cross-tool data workflow (PowerQuery → Python → Power BI)



## About

**Ina Louise Magno** — Data Analyst | Chemical Engineering graduate (UPLB)  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/ina-louise-magno)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/chimkeninasal)
