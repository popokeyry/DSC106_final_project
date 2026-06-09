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

### Combined Dataset: `climate_signals_like_actually.csv`

We merged the above sources into a single clean dataset:

- **Rows:** 360
- **Columns:** 8
- **Countries:** 15
- **Years:** 2000–2023 (24 years per country)

**Columns:**

| Column | Description |
|---|---|
| `Year` | 2000–2023 |
| `Country` | One of 15 countries |
| `Avg Temperature in Celsius` | Annual mean temperature (Berkeley Earth) |
| `CO2 Emissions (Tons/Capita)` | Per-capita CO₂ emissions |
| `Sea Level Rise (cm)` | Global mean sea level rise from 1993 baseline |
| `Population` | Annual population |
| `Renewable Energy (%)` | Share of electricity from renewables |
| `Extreme Weather Events` | Annual count of natural disasters (EM-DAT) |

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
