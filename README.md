# Data for: Niche conservatism of thermal traits operates more strongly at the subspecies than species level in an alpine mammal

**Authors:** Peter D. Billman, Mark C. Urban

This repository contains the data files used in the analyses described in the manuscript. Two processed files are included; one shapefile folder of approximate lineage boundaries is included; and one climate raster must be downloaded by users separately (see below).

R packages used include ape, phytools, geiger, and OUwie. 

---

## Files in this repository

### 1. `Thermal_Thresholds_by_Transect.csv`

Estimated observed upper thermal limits for American pika (*Ochotona princeps*) populations across elevational transects in four lineages. Thermal limits were estimated as the temperature at which predicted occupancy probability falls to 0.50, derived from logistic regression models fit to presence–absence records along each transect. Analyses exclude the Cascade Range and Central Utah lineages, which lack systematic elevational transect data with verified absences.

| Column | Description |
|--------|-------------|
| `Predictor` | Climate variable used in the logistic regression model. `Tave_sm_Avg` = mean summer temperature (June–August), averaged over a 5-year window prior to sampling (or a 10-year decadal average for Sierra Nevada sites). |
| `Transect` | Name of the elevational transect (Rocky Mountain lineages) or EPA Level III ecoregion (Sierra Nevada). |
| `Threshold` | Estimated observed upper thermal limit (°C): the temperature at which predicted occupancy probability = 0.50, calculated as −intercept/slope from the fitted logistic curve. |
| `Intercept` | Intercept of the fitted logistic regression model. |
| `Slope` | Slope of the fitted logistic regression model. |
| `Lineage` | Genetic lineage assignment: Central Rockies, Northern Rockies, Sierra Nevada, or Southern Rockies. |
| `Data Source` | Original source of the occurrence records. P. Billman = surveys conducted 2022–2025 for Central, and Southern Rocky Mountain lineages; Billman et al. 2021 = Northern Rockies transect data from https://doi.org/10.1111/gcb.15793; Millar et al. 2018 = published Sierra Nevada database. |

**n = 65 transects** across four lineages (Northern Rockies: 36, Southern Rockies: 20, Central Rockies: 5, Sierra Nevada: 4).

---

### 2. `Population_MeanMass_by_Ecoregion.csv`

Population-level mean body mass estimates for American pika across all six lineages, derived from georeferenced museum specimen records compiled by Westover and Smith (2020) [https://doi.org/10.1093/jmammal/gyaa041]. Populations are defined as ≥ 10 adult individuals (> 91.6 g) collected within 10 km of one another and within the same mountain range.

| Column | Description |
|--------|-------------|
| `population_id` | Unique numeric identifier for each population. |
| `n_samples` | Number of museum specimens used to calculate the population mean. |
| `mean_mass` | Population mean body mass (g). |
| `sd_mass` | Standard deviation of body mass within the population (g). |
| `Lineage` | Genetic lineage assignment: Cascades, Central Rockies, Central Utah, Northern Rockies, Sierra Nevada, or Southern Rockies. |
| `approx_lon` | Approximate longitude of the population centroid (decimal degrees, WGS84). |
| `approx_lat` | Approximate latitude of the population centroid (decimal degrees, WGS84). |

**n = 88 populations** across six lineages (Northern Rockies: 22, Sierra Nevada: 20, Central Rockies: 14, Southern Rockies: 12, Cascades: 13, Central Utah: 7).

Body mass data were originally published in: Westover, M. L., & Smith, F. A. (2020). Investigating the role of environment in pika (*Ochotona*) body size patterns across taxonomic levels, space, and time. *Journal of Mammalogy*, 101(3), 804–816.

---

### 3. `LineagesSHP/` (folder)

A shapefile of the approximate geographic extents of the six American pika lineages in western North America, based on phylogeographic delineations in Schmidt et al. (2024). Used to extract broad-scale climate conditions within each lineage's range, and to assign data (thermal limit + body mass) to lineages.

The folder contains the standard shapefile components (`.shp`, `.shx`, `.dbf`, `.prj`, and associated files). Load in R with `sf::st_read("LineagesSHP/Lineages_named.shp")`.

Schmidt, D. A., Galbreath, K. E., & Russello, M. A. (2024). Phylogenomics of American pika (*Ochotona princeps*) lineage diversification. *Molecular Phylogenetics and Evolution*, 193, 108030.

---

## External climate data (not included)

### `Normal_1991_2020_Tave_sm.tif`

Mean summer temperature (June–August) 1991–2020 climate normals, obtained from **ClimateNA** (Wang et al. 2016). This raster was used to characterize broad-scale thermal environments within each lineage polygon and to extract site-level temperature covariates for thermal limit estimation. This file was too large to upload to github.

**To obtain this file:**
1. Go to [https://climatena.ca](https://climatena.ca)
2. Navigate to the **Spatial Data** tab adn choose → **1991–2020 Normal Period**
3. Select the variable **Tave_sm** (mean summer temperature)
4. Download the raster for North America and save it as to your computer.

Wang, T., Hamann, A., Spittlehouse, D., & Carroll, C. (2016). Locally downscaled and spatially customizable climate data for historical and future periods for North America. *PLOS ONE*, 11(6), e0156720.

---

## Citation

If you use these data, please cite the associated manuscript:

> Billman, P.D. and Urban, M.C. (*in review*). Niche conservatism of thermal traits operates more strongly at the subspecies than species level in an alpine mammal.

Please also cite the original sources for body mass data (Westover & Smith 2020) and Sierra Nevada occurrence records (Millar et al. 2018) as appropriate, as well as Wang et al. 2016 for climate data.
