# Climate Variability and Crop Yield Stability

## 1. Project Overview

This project investigates the relationship between interannual climate variability and crop yield instability across five countries from 2000 to 2023.

The study examines whether greater temperature and precipitation variability is associated with greater year-to-year instability in crop yields and compares the climatic sensitivity of three major cereal crops.

## 2. Research Questions

- Is greater interannual climate variability associated with greater crop yield instability?
- Which crop shows the strongest association with climate anomalies?
- How have climate variability and crop yield instability changed over time?

## 3. Study Scope

- **Countries:** India, China, United States, Brazil and Australia.
- **Crops:** Maize, rice and wheat.
- **Study period:** 2000–2023.
- **Yield observations:** 360 country-crop-year observations.
- **Climate observations:** 120 country-year observations.

## 4. Data Sources

The original raw datasets are not included in this repository. They can be accessed from the official sources linked below.

### 4.1 FAOSTAT — Crop Yield Data

FAOSTAT provides agricultural statistics, including crop yield, production and harvested area.

- **Used for:** Annual national yield data for maize, rice and wheat across the five study countries.
- **Study period:** 2000–2023.
- **Unit:** kg/ha.
- **Source:** https://www.fao.org/faostat/en/#data/QCL

### 4.2 ERA5-Land — Climate Data

ERA5-Land provides historical land-surface and climate data, including temperature and precipitation.

- **Used for:** Monthly 2 m temperature and total precipitation data to construct annual climate indicators.
- **Study period:** 2000–2023.
- **Source:** https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land-monthly-means

### 4.3 CHIRPS — Independent Precipitation Validation

CHIRPS combines satellite observations with ground-based station information to provide gridded precipitation estimates.

- **Used for:** Independently comparing India's ERA5-Land precipitation estimates with CHIRPS rainfall estimates for 2021–2023.
- **Role:** Validation and consistency check; CHIRPS is not the primary climate dataset.
- **Source:** https://www.chc.ucsb.edu/data/chirps

### 4.4 Natural Earth — Country Boundaries

Natural Earth provides geographic boundary data for countries.

- **Used for:** Creating country masks for extracting country-level climate information.
- **Source:** https://www.naturalearthdata.com/downloads/10m-cultural-vectors/10m-admin-0-countries/

## 5. Repository Structure

- `data/processed/` — cleaned climate and crop-yield datasets used in the analysis.
- `notebooks/` — notebooks for multi-country climate analysis, CHIRPS validation and exploratory analysis.
- `results/figures/` — generated figures.
- `results/tables/` — exported analysis results and validation tables.
- `presentation/` — final mid-evaluation presentation.
- `requirements.txt` — Python package dependencies.

## 6. Methodology

1. Clean and filter crop-yield data for the selected countries, crops and years.
2. Process monthly ERA5-Land climate data and derive annual indicators.
3. Quantify temperature variability using detrended temperature anomalies and precipitation variability using the coefficient of variation.
4. Measure crop yield instability using the standard deviation of residuals from a linear trend fitted to log yield.
5. Examine associations using Pearson and Spearman correlations.
6. Fit exploratory crop-specific models relating standardized climate anomalies to detrended yield.
7. Examine changes using rolling 10-year windows.
8. Compare ERA5-Land precipitation against CHIRPS estimates for India.

## 7. Important Data Processing Note

The ERA5-Land monthly averaged precipitation product has a documented issue affecting accumulated variables during part of the September 2022–February 2024 period. The affected precipitation series was corrected using the appropriate ERA5-Land monthly product before the final analysis was rebuilt through 2023.

The final processed datasets and validation tables are included in this repository. The original raw files are not included, so reproducing the full workflow from scratch requires obtaining the source datasets and applying the documented processing steps.

## 8. Main Findings

- Precipitation variability shows a positive association with crop yield instability, although the overall relationship is strongly influenced by Australia.
- Temperature variability shows a weaker and less consistent relationship with yield instability.
- Wheat shows the strongest pooled association with climate anomalies among the three crops examined.
- Rice is generally the most stable crop in the selected country comparisons.
- Changes in climate variability differ across countries; there is no uniform increase across all five countries.

These are exploratory associations and do not establish causation.

## 9. Running the Project

1. Clone or download this repository.
2. Install the packages listed in `requirements.txt`.
3. Obtain the raw datasets from the linked sources if reproducing the analysis from scratch.
4. Open the notebooks in Jupyter Notebook or VS Code.
5. Check dataset paths and run the notebooks in the appropriate order.

The included processed CSV files support inspection of the final analysis without downloading the raw datasets.

## 10. Limitations

- The analysis uses national-level climate indicators rather than crop-specific growing-season climate variables.
- Only five countries and three crops are included.
- Climate is one of several factors influencing crop yield.
- Correlation and regression results are exploratory and do not prove causal relationships.