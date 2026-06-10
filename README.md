# DSC106_final_project
# 🌍 Are We Turning the Tide?
### Two Decades of Climate Signals — An Explorable Explanation

**DSC 106 Final Project · Climate Cartographers**
Aaditya Aswadhati · Nainika Neerukonda · Ryan Atienza

---

## 🔗 Links

| | |
|---|---|
| **Live Webpage** | https://popokeyry.github.io/DSC106_final_project/ |
| **GitHub Repository** | https://github.com/popokeyry/DSC106_final_project |

---

## 📌 Project Overview

Are the countries building renewable energy actually cutting emissions, and what have two decades of climate impacts looked like in the meantime?

This project tracks **five climate signals** across **15 countries** from **2000 to 2023**, using credible, publicly available datasets. It is built as an explorable explanation using D3.js v7, combining scrollytelling, interactive predictions, a quiz, and a data sandbox to guide readers through the question and let them discover their own answers.

---

## ✨ Features

- **Prediction Game** — Before seeing the data, readers draw their own guess at the average warming trend (2000–2023). Their sketch is then compared against the real Berkeley Earth signal.
- **Scrollytelling** — Three sticky-chart chapters walk through temperature divergence across countries, the renewables-vs-emissions relationship over time (2000 → 2012 → 2023), and global sea level rise alongside extreme weather events.
- **Direction-of-Travel Quadrant** — A scatter plot showing each country's 20-year slope: did renewables rise? Did emissions fall? Nine of fifteen landed in the "win–win" corner.
- **Commit-Then-Reveal Quiz** — Four questions where readers must commit to an answer before seeing whether the data confirms or surprises their mental model.
- **Exploration Sandbox** — Plot any two indicators against each other for any year, or rank all fifteen countries on any metric.

---

## 📊 Dataset

### Why We Rebuilt the Dataset

We originally used a Kaggle dataset, but during analysis discovered severe data quality issues — for example, the U.S. population jumping from ~300 million in 2001 to ~1.1 billion in 2002. These inconsistencies were widespread and not immediately obvious. Once identified, we made the decision to replace the dataset entirely with data sourced from more credible, well-maintained providers, while keeping the same 15-country framework.

# Climate Signals Dataset — README

## Overview

This dataset combines five real-world climate and energy sources into a single clean file covering **15 countries** across **23 years (2000–2022)**. The result is **345 rows × 8 columns** — one row per country per year.

**Output file:** `climate_signals_real.csv`

---

## Columns

| Column | Unit | Source |
|---|---|---|
| `Year` | integer (2000–2022) | derived |
| `Country` | string | derived |
| `Avg Temperature (°C)` | degrees Celsius, annual mean | Berkeley Earth / World Bank CRU |
| `CO2 Emissions (Tons/Capita)` | metric tons per person | Our World in Data |
| `Sea Level Rise (cm)` | cm above 1993 baseline | NASA-SSH |
| `Population` | integer (persons) | Our World in Data |
| `Renewable Energy (%)` | % of total energy consumption | Our World in Data |
| `Extreme Weather Events` | count of natural disaster events | EM-DAT |

---

## Countries

Argentina, Australia, Brazil, Canada, China, France, Germany, India, Indonesia, Japan, Mexico, Russia, South Africa, UK, USA

Short names are used in the CSV. The name mapping for each source is documented in the preprocessing section below.

---

## Data Sources

### 1. Temperature — 13 countries
- **Dataset:** Berkeley Earth Country-Level Annual Mean Surface Temperature
- **File used:** `combined_temperature.csv`
- **URL:** https://berkeleyearth.org/data/
- **Coverage:** 1901–2022; annual means

### 2. Temperature — China and India only
- **Dataset:** World Bank Climate Change Knowledge Portal — CRU TS4.08 Annual Mean Temperature
- **File used:** `cru-x0_5_timeseries_tas_timeseries_annual_1901-2023_mean_historical_cru_ts4_08_mean__1_.xlsx`
- **URL:** https://climateknowledgeportal.worldbank.org/
- **Underlying source:** CRU TS4.08 (Climatic Research Unit, University of East Anglia)
- **Coverage:** 1901–2023; annual means
- **Note:** Used for China and India only, as these were absent from the Berkeley Earth combined file

### 3. CO₂ Emissions and Population
- **Dataset:** Our World in Data CO₂ and Greenhouse Gas Emissions
- **File used:** `owid-co2-data.csv`
- **URL:** https://github.com/owid/co2-data
- **Underlying source:** Global Carbon Project
- **Coverage:** 1750–2023; annual

### 4. Renewable Energy Share
- **Dataset:** Our World in Data Renewable Energy Share
- **File used:** `renewable-share-energy.csv`
- **URL:** https://ourworldindata.org/renewable-energy
- **Underlying source:** BP Statistical Review of World Energy
- **Coverage:** 1965–2023; annual
- **Definition:** Renewables as a percentage of total primary energy consumption

### 5. Extreme Weather Events
- **Dataset:** EM-DAT International Disaster Database
- **File used:** `public_emdat_2026-05-28.xlsx`
- **URL:** https://www.emdat.be/
- **Publisher:** Centre for Research on the Epidemiology of Disasters (CRED), Université catholique de Louvain
- **Access date:** 2026-05-28

### 6. Sea Level Rise
- **Dataset:** NASA-SSH Global Mean Sea Level from Simple Gridded Sea Surface Height, Standardized Reference Missions Only, Version 1
- **URL:** https://doi.org/10.5067/NSIND-GMSV1
- **Coverage:** 1993–2026; ~7-day observations
- **Citation:** NASA-SSH. 2025. Global Mean Sea Level from Simple Gridded Sea Surface Height from Standardized Reference Missions Only Version 1. PO.DAAC, CA, USA.

---

## Preprocessing Steps

### Step 1 — Temperature: 13 countries (`combined_temperature.csv`)

Filtered to rows where `Country` matched one of the 13 countries below. Extracted the `Annual Mean` column. Filtered to years 2000–2022.

**Country name mapping:**

| Source name | CSV name |
|---|---|
| United Kingdom | UK |
| United States | USA |
| Russian Federation | Russia |
| Argentina | Argentina |
| Australia | Australia |
| Brazil | Brazil |
| Canada | Canada |
| France | France |
| Germany | Germany |
| Indonesia | Indonesia |
| Japan | Japan |
| Mexico | Mexico |
| South Africa | South Africa |

---

### Step 2 — Temperature: China and India (`cru-x0_5_...xlsx`)

China and India were not present in the Berkeley Earth combined file. Their values were sourced separately from the World Bank Climate Portal (CRU TS4.08).

The file has one row per country, with year columns formatted as `YYYY-07` (e.g. `2000-07`). Values are annual mean surface temperature in °C.

Extracted by matching ISO codes `CHN` (China) and `IND` (India) and reading columns `2000-07` through `2023-07`.

**China annual mean temperature (°C) — World Bank CRU TS4.08:**

| Year | Temp | Year | Temp | Year | Temp |
|---|---|---|---|---|---|
| 2000 | 7.25 | 2008 | 7.63 | 2016 | 7.95 |
| 2001 | 7.61 | 2009 | 7.81 | 2017 | 8.13 |
| 2002 | 7.83 | 2010 | 7.59 | 2018 | 7.79 |
| 2003 | 7.54 | 2011 | 7.37 | 2019 | 8.04 |
| 2004 | 7.77 | 2012 | 7.09 | 2020 | 7.96 |
| 2005 | 7.50 | 2013 | 7.76 | 2021 | 8.24 |
| 2006 | 7.99 | 2014 | 7.72 | 2022 | 8.13 |
| 2007 | 8.18 | 2015 | 8.00 | 2023 | 8.40 |

**India annual mean temperature (°C) — World Bank CRU TS4.08:**

| Year | Temp | Year | Temp | Year | Temp |
|---|---|---|---|---|---|
| 2000 | 24.80 | 2008 | 24.82 | 2016 | 25.36 |
| 2001 | 24.93 | 2009 | 25.57 | 2017 | 25.23 |
| 2002 | 25.20 | 2010 | 25.51 | 2018 | 25.11 |
| 2003 | 24.93 | 2011 | 24.88 | 2019 | 25.02 |
| 2004 | 25.03 | 2012 | 24.83 | 2020 | 24.86 |
| 2005 | 24.77 | 2013 | 24.71 | 2021 | 25.07 |
| 2006 | 25.03 | 2014 | 24.86 | 2022 | 25.18 |
| 2007 | 25.06 | 2015 | 24.98 | 2023 | 25.02 |

---

### Step 3 — CO₂ and Population (`owid-co2-data.csv`)

Filtered to rows where `country` matched one of the 15 countries. Extracted columns `co2_per_capita` → `CO2 Emissions (Tons/Capita)` and `population` → `Population`. Filtered to years 2000–2023. Rows with empty `co2_per_capita` were dropped.

**Country name mapping:**

| Source name | CSV name |
|---|---|
| United States | USA |
| United Kingdom | UK |
| Russia | Russia |
| All others | same as source |

---

### Step 4 — Renewable Energy (`renewable-share-energy.csv`)

Filtered to rows where `Entity` matched one of the 15 countries. Extracted the `Renewables` column. Filtered to years 2000–2023. Applied the same country name mapping as Step 3.

---

### Step 5 — Extreme Weather Events (`public_emdat_2026-05-28.xlsx`)

- Loaded the default sheet
- Filtered to `Disaster Group == 'Natural'` (excludes technological and biological events)
- Filtered to `Start Year` between 2000 and 2023 inclusive
- Counted the number of qualifying events per country per year
- Country-year combinations with zero events recorded as `0`

**Country name mapping:**

| Source name | CSV name |
|---|---|
| United States of America | USA |
| United Kingdom of Great Britain and Northern Ireland | UK |
| Russian Federation | Russia |
| All others | same as source |

---

### Step 6 — Sea Level Rise (NASA-SSH)

Source data is global mean sea level (GMSL) in centimetres relative to a 1993 baseline, measured approximately every 7 days. Annual mean values were computed by averaging all observations within each calendar year. The same value is assigned to all 15 countries for a given year, as sea level rise is a global phenomenon.

| Year | cm | Year | cm | Year | cm |
|---|---|---|---|---|---|
| 2000 | 2.28 | 2008 | 4.11 | 2016 | 7.16 |
| 2001 | 2.83 | 2009 | 4.49 | 2017 | 7.23 |
| 2002 | 2.76 | 2010 | 4.74 | 2018 | 7.54 |
| 2003 | 3.15 | 2011 | 4.55 | 2019 | 8.22 |
| 2004 | 3.17 | 2012 | 5.42 | 2020 | 8.32 |
| 2005 | 3.46 | 2013 | 5.49 | 2021 | 8.91 |
| 2006 | 3.64 | 2014 | 5.95 | 2022 | 9.41 |
| 2007 | 3.55 | 2015 | 6.62 | - | - |

---

### Step 7 — Merging

All sources were merged on `Country` and `Year` to produce one row per country-year combination (345 rows total). Sea level was joined on `Year` only. All 345 rows in the final CSV are complete with no missing values.

---

## Known Limitations

- **Sea level rise is global**, not country-level. It is the same value for all 15 countries in a given year, representing a shared physical signal rather than a local measurement.
- **Extreme weather event counts** reflect EM-DAT recorded natural disaster events only. EM-DAT records are not exhaustive — smaller or less-documented events may be under-reported, particularly in earlier years.
- **Renewable energy %** includes large hydropower, which means countries like Brazil (heavily hydro-dependent) show high renewable shares independently of recent wind/solar buildout.
- **Two temperature sources are combined.** China and India use World Bank CRU TS4.08 while the other 13 countries use Berkeley Earth. Both are gridded observational products but use different methodologies, so small systematic differences may exist at country level.

### Sources

| Signal | Source |
|---|---|
| CO₂ Emissions (Tons/Capita) | [Our World in Data](https://ourworldindata.org/co2-emissions) (Global Carbon Project) |
| Population | [Our World in Data](https://ourworldindata.org/co2-emissions) |
| Average Temperature (°C) | [Berkeley Earth](https://berkeleyearth.org/data/) — country-level annual means |
| Renewable Energy (%) | [Our World in Data](https://ourworldindata.org/renewable-energy) (BP Statistical Review) |
| Extreme Weather Events | [EM-DAT](https://www.emdat.be/) — International Disaster Database |
| Sea Level Rise (cm) | [NASA-SSH](https://sealevel.nasa.gov/) — Global Mean Sea Level, satellite altimetry |

All sources are publicly accessible.

---

## 🛠 Built With

- [D3.js v7](https://d3js.org/)
- Vanilla HTML / CSS / JavaScript
- GitHub Pages (hosting)

---

## 🗂 Repository Structure

```
DSC106_final_project/
├── index.html                        # Main webpage
├── climate_signals_like_actually.csv # Combined dataset
├── js/                               # D3 visualization scripts
├── css/                              # Styles
└── README.md
```

---

## 📝 Key Finding

Nine of fifteen countries studied grew their renewable energy share *and* cut per-capita CO₂ emissions over the two decades; genuine, measurable progress. But global mean sea level rose over 7 cm and continues accelerating, and temperature anomalies show no sign of leveling off. Progress is real. It is not yet enough.

---

*DSC 106 · Data Visualization · UC San Diego*
