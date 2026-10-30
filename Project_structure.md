# Capstone_project_Lorenzo (Title to confirm)

![Alt Text](/Capstone_project_lorenzo/images/squid_meme.png)

#### My project investigates how Berlin's summer heat conditions in 2026 compared with 2025, focusing on temperature patterns, environmental quality and neighbourhood characteristics that may influence heat exposure. The aim is to identify meaningful patterns and explore how the findings could support future urban heat adaptation.


### Who are the stakeholders?

![Alt Text](/Capstone_project_lorenzo/images/simpson_gif.gif)

The main stakeholders are Berlin's policymakers and public authorities responsible for urban planning, climate adaptation, environmental protection and public health.

The findings could help these stakeholders better understand environmental patterns during hot periods, identify areas for further investigation and inform future heat-mitigation strategies and resource allocation.


### Main research question:
![Alt Text](/Capstone_project_lorenzo/images/hot_meme.png)
- How did Berlin's 2026 heatwave periods compare with 2025 in terms of temperature and environmental quality, and how might neighbourhood characteristics help explain differences in heat exposure?
### Supporting questions:
- How did the frequency, intensity and duration of hot periods differ between 2025 and 2026?
- How did air-pollutant concentrations and sampled bathing-water quality vary during hotter and cooler periods?
- How do vegetation, impervious surfaces and population density vary across Berlin, and what can these characteristics tell us about potential heat exposure?
### Secondary questions, subject to data availability:
- Did electricity demand or water supply increase during hotter periods, compared with cooler or comparable periods?
- Was there any correlation of increased death rates vs higher temperatures?

### Core analysis

- Heat patterns: compare daily maximum and minimum temperatures, hot-day counts and heatwave duration in 2025 and 2026 specifically from May/June until September.
- Air quality: analyse available pollutants such as ozone, PM2.5, PM10 and NO₂, comparing hotter and less-hot days while checking data coverage.
- Bathing-water quality: examine bacterial, oxygen level, PH measurements and water temperature at the selected bathing sites, relating samples to recent temperature and rainfall.
- Urban context: compare tree cover, impervious surfaces and population density to identify areas that may be more vulnerable to heat.

### Secondary/optional extended points to analyse

- Electricity demand and water supply, depending on whether suitable 2025–2026 time-series data become available.
- Mortality or health indicators, if reliable data are available.
- Building age and heat retention, only if meaningful measure of actual heat exposure or thermal performance can be obtained.
- Comparisons with other european cities or a longer historical period.

### Methodology
![alt text](/Capstone_project_lorenzo/images/process_meme.png)
- Data collection and validation: Collect weather, air-quality, bathing-water, land-cover and population data from official sources. Check completeness, consistency, time coverage and geographic coverage before analysis.
- Data preparation: clean and standardise dates, units, station identifiers and geographic boundaries. Aggregate hourly weather and air-quality measurements to daily values where appropriate.
- Comparative analysis: compare summer 2025 and 2026, and investigate differences between hotter and less-hot periods. Use appropriate averaging periods for each pollutant and account for missing measurements.
- Spatial analysis: combine population density, tree-cover and impervious-surface data to identify neighbourhood characteristics associated with potentially higher heat exposure.
- Visualisation and communication: use Python for data preparation, exploratory analysis and statistical comparisons, then Tableau or Streamlit to present the findings in an accessible, stakeholder-oriented dashboard.

### KPIs:
![Alt Text](/Capstone_project_lorenzo/images/kpi_meme.png)
- Number of hot days: how often high temperatures occurred.
- Longest consecutive hot period: how persistent the heat was.
- Air quality: mean pollutant concentration on hot vs. comparison days,	to check whether pollution levels differed with heat.
- Bathing water: bacterial measurements and number of samples exceeding the relevant benchmark, to check whether sampled water quality raised concerns.
- Urban context: tree-cover and impervious-surface shares, to check how green or built-up an area is.
- Population: residents in areas meeting defined exposure criteria, how many people may be affected, if spatial data support the estimate.
- Resource demand — optional: percentage change in electricity load or water supply.
- Heat and mortality - optional: compare mortality during defined heatwave periods with a suitable baseline, accounting where possible for seasonality, long-term trends and population differences.

### Data sources:
![Alt Text](/Capstone_project_Lorenzo/images/data_meme.png)

Weather: [DWD Open Data](https://opendata.dwd.de/) and [Meteostat](https://meteostat.net/en/) <BR>
Air quality: [Berlin Air Quality Network](https://luftdaten.berlin.de/lqi) <BR>
Bathing-water quality: [Berlin Water Portal](https://wasserportal.berlin.de/start.php) and [historical measurements](https://wasserportal.berlin.de/recherche.php) <BR>
Land cover and vegetation: [Copernicus Urban Atlas 2021](https://land.copernicus.eu/en/products/urban-atlas/urban-atlas-2021), [Imperviousness](https://land.copernicus.eu/en/products/high-resolution-layer-imperviousness) and [Tree Cover Density](https://land.copernicus.eu/en/products/high-resolution-layer-forests-and-tree-cover/tree-cover-density-2018-present-raster-100-m-europe-yearly) <BR>
Population: [German Census 2022](https://www.destatis.de/DE/Themen/Gesellschaft-Umwelt/Bevoelkerung/Zensus2022/_inhalt.html) <BR>
Mortality — optional: [Destatis mortality statistics](https://www.destatis.de/DE/Themen/Gesellschaft-Umwelt/Bevoelkerung/Sterbefaelle-Lebenserwartung/Publikationen/Downloads-Sterbefaelle/statistischer-bericht-sterbefaelle-tage-wochen-monate-aktuell-5126109.html) <BR>
Water supply — optional: [Berlin Water Company key figures](https://www.bwb.de/de/kennzahlen.php); a request for more recent data has been sent. <BR>
Electricity demand — optional: [Stromnetz Berlin disclosures](https://www.stromnetz.berlin/en/about-us/disclosure-requirements/enwg/); a request for more recent data has been sent. <BR>

Data have been obtained through API calls and manual downloads. Some datasets required selecting specific time periods, geographic areas and variables. Data requested from external organisations are still subject to availability and delivery timelines.