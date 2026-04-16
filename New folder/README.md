# Flood Risk Mapping & Analysis — Lagos State, Nigeria
### Focus: Agege · Ikeja · Alimosho Local Government Areas

![Python](https://img.shields.io/badge/Python-3.9+-blue?logo=python&logoColor=white)
![GeoPandas](https://img.shields.io/badge/GeoPandas-0.13+-green)
![Folium](https://img.shields.io/badge/Folium-0.14+-yellowgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## Project Overview

Lagos State, Nigeria, is one of West Africa's most flood-vulnerable megacities. Rapid urbanisation, inadequate drainage infrastructure, low-lying coastal and inland terrain, and intense seasonal rainfall (averaging 1,400–1,700 mm/year) combine to make flooding a recurring humanitarian and economic crisis.

This project performs a **multi-criteria geospatial flood risk assessment** of three key Local Government Areas (LGAs):

| LGA | Area (km²) | Est. Population |
|-----|-----------|----------------|
| **Agege** | ~23 | ~1.2 million |
| **Ikeja** | ~46 | ~0.7 million |
| **Alimosho** | ~185 | ~1.9 million |

Using a **Weighted Overlay Model (WOM)**, four environmental and socioeconomic factors are combined into a single **Flood Risk Index (FRI)** that classifies zones from *Very Low* to *Very High* risk.

---

## 🎯 Workflow

1. Acquired and process spatial data for the three LGAs
2. Engineer flood-risk proxy indicators (elevation, rainfall, population density, land-use)
3. Normalise and combine indicators using a weighted overlay approach
4. Visualise results as both static (PNG) and interactive (HTML) maps
5. Derive actionable insights for urban planners and emergency managers

---



## 🧰 Tools & Libraries

| Library | Purpose |
|---------|---------|
| **GeoPandas** | Spatial data I/O, CRS management, geometric operations |
| **Shapely** | Geometric primitives and spatial predicates |
| **Pandas / NumPy** | Tabular data processing and numerical computation |
| **Matplotlib / Contextily** | Static map rendering with basemap tiles |
| **Folium** | Interactive Leaflet.js maps via Python |
| **Rasterio** | Raster (DEM) data handling |
| **Scikit-learn** | Min-Max normalisation of risk factors |
| **Jupyter Notebook** | Literate programming environment |

---

## 📐 Methodology

### 1. Data Acquisition & Simulation

### 2. Feature Engineering
Each raw variable is converted to a **risk score (0–1)**:

| Factor | Direction | Rationale |
|--------|-----------|-----------|
| Elevation | Inverse (lower = higher risk) | Water accumulates at low points |
| Rainfall | Direct (higher = higher risk) | Greater precipitation input |
| Population Density | Direct (denser = higher impact) | More people exposed |
| Impervious Cover | Direct (more built-up = higher risk) | Reduced infiltration capacity |

### 3. Weighted Overlay Model

```
FRI = w₁·(1 − Elevation_norm) + w₂·Rainfall_norm + w₃·PopDensity_norm + w₄·LandUse_norm
```

Default weights reflect established hydrological literature:

| Weight | Factor | Value |
|--------|--------|-------|
| w₁ | Elevation | 0.35 |
| w₂ | Rainfall | 0.25 |
| w₃ | Population Density | 0.20 |
| w₄ | Land Use (Imperviousness) | 0.20 |

### 4. Risk Classification

| FRI Range | Class | Colour |
|-----------|-------|--------|
| 0.00–0.20 | Very Low | `#1a9850` |
| 0.20–0.40 | Low | `#91cf60` |
| 0.40–0.60 | Moderate | `#fee08b` |
| 0.60–0.80 | High | `#fc8d59` |
| 0.80–1.00 | Very High | `#d73027` |

---


## Outputs

| Output | Description |
|--------|-------------|
| `flood_risk_static.png` | Multi-panel figure: individual risk factors + composite FRI choropleth |
| `flood_risk_interactive.html` | Folium map with hover tooltips, layer toggles, and colour-coded LGA zones |

---

## 📊 Key Findings (Preview)

- **Alimosho** contains the largest contiguous high-risk zones due to low-lying terrain and high population density
- **Agege** shows concentrated very-high-risk pockets along simulated creek corridors
- **Ikeja** (state capital) presents moderate risk overall but with localised hotspots near drainage pinch-points
- Approximately **38% of the combined study area** scores ≥ 0.6 (High or Very High risk)

---

## ⚠️ Limitations


- Static weights are subjective; AHP or ML-derived weights preferred for production
- Dynamic flood modelling (HEC-RAS, LISFLOOD) not included
- Temporal variation (seasonal flooding cycles) not captured

---

## 🔭 Future Work

- Integrate live CHIRPS rainfall API and SRTM 30m DEM
- Apply SAR-based flood extent mapping (Sentinel-1)
- Train a Random Forest classifier on historical flood event records
- Deploy as a real-time web dashboard (Streamlit / Dash)

---

## 📚 References

1. Nkwunonwo, U. C. et al. (2020). *Urban flood modelling combining cellular automata framework with semi-implicit finite difference numerical formulation.* Journal of African Earth Sciences.
2. Komolafe, A. A. et al. (2018). *A review of flood risk analysis in Nigeria.* Earth-Science Reviews.
3. Lagos State Emergency Management Agency (LASEMA) Flood Reports, 2019–2023.
4. Ajibade, L. T. et al. (2021). *Flood vulnerability assessment in Lagos metropolis.* International Journal of Disaster Risk Reduction.

---

## 👤 Author

**Patrick Nkwachukwu Ezeh**  

---
*This project uses simulated data structured to reflect real geographic and hydrological patterns. It is intended as a portfolio demonstration and should not be used for operational emergency management without validated real-world datasets.*
