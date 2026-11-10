
### Data contained into meteostat datasets:

| Parameter | Description | Type |
|---|---|---|
| date | The date string (YYYY-MM-DD) | String |
| tavg | The average air temperature in °C | Float |
| tmin | The minimum air temperature in °C | Float |
| tmax | The maximum air temperature in °C | Float |
| prcp | The daily precipitation total in mm | Float |
| snow | The maximum snow depth in mm | Integer |
| wdir | The average wind direction in degrees (°) | Integer |
| wspd | The average wind speed in km/h | Float |
| wpgt | The peak wind gust in km/h | Float |
| pres | The average sea-level air pressure in hPa | Float |
| tsun | The daily sunshine total in minutes (m) | Integer |

### Data contained into DWD datasets:

| Column name | Description | UOM | Type | Format |
|---|---|---|---|---|
| STATIONS_ID | Station ID | — | VARCHAR2 | — |
| MESS_DATUM | Reference date | — | NUMBER | YYYYMMDD |
| QN_3 | Quality level of the following columns | — | NUMBER | Numerical code |
| FX | Daily maximum of wind gust | m/s | NUMBER | 9990.0 |
| FM | Daily mean of wind velocity | m/s | NUMBER | 9990.0 |
| QN_4 | Quality level of the following columns | — | NUMBER | Numerical code |
| RSK | Daily precipitation height | mm | NUMBER | 9990.0 |
| RSKF | Precipitation form | — | NUMBER | Numerical code |
| SDK | Daily sunshine duration | h | NUMBER | 9990.0 |
| SHK_TAG | Daily snow depth | cm | NUMBER | 9990.0 |
| NM | Daily mean of cloud cover | 1/8 | NUMBER | 9990.0 |
| VPM | Daily mean of vapor pressure | hPa | NUMBER | 9990.0 |
| PM | Daily mean of pressure | hPa | NUMBER | 9990.0 |
| TMK | Daily mean of temperature | °C | NUMBER | 9990.0 |
| UPM | Daily mean of relative humidity | % | NUMBER | 9990.0 |
| TXK | Daily maximum of temperature at 2 m height | °C | NUMBER | 9990.0 |
| TNK | Daily minimum of temperature at 2 m height | °C | NUMBER | 9990.0 |
| TGK | Daily minimum of air temperature at 5 cm above ground | °C | NUMBER | 9990.0 |

### Water quality datasets

| Key | Description | Unit / Format | Notes |
|---|---|---|---|
| station_id | Measuring station ID | Text | Unique station identifier |
| station_name | Measuring station name | Text | Name of the monitoring location |
| water_body | Water body name | Text | Lake or other water body |
| longitude | Longitude | Decimal degrees | WGS 84 |
| latitude | Latitude | Decimal degrees | WGS 84 |
| coordinate_reference_system | Coordinate reference system | Text | WGS 84 |
| measurement_note | Measurement interpretation note | Text | Values preceded by `<` are below the analytical quantification limit |
| bathing_water_quality | Bathing-water quality warning level | Categorical | Warning assessment; not a numerical measurement |
| coliform_bacteria | Total coliform bacteria concentration | KBE/100 ml | Colony-forming units per 100 ml |
| cyanobacteria_chlorophyll_a | Chlorophyll-a concentration associated with cyanobacteria | µg/l | Indicator associated with cyanobacteria; not a direct cell count |
| e_coli | Escherichia coli concentration | KBE/100 ml | Indicator of faecal contamination |
| intestinal_enterococci | Intestinal enterococci concentration | KBE/100 ml | Indicator of faecal contamination |
| water_transparency_depth | Water transparency depth | m | Visibility depth in water |
| water_temperature | Water temperature | °C | Temperature in degrees Celsius |

KBE means Koloniebildende Einheiten — equivalent to CFU (colony-forming units). It is a count of viable bacteria expressed per 100 ml.
Sampling dates on the datasets are irregular, taken approximately every 2-3 weeks, from May until September
More info can be found below:

Info regarding bathing waters classification criteria: https://www.berlin.de/lageso/gesundheit/gesundheitsschutz/badegewaesser/eu-einstufung/

https://www.berlin.de/lageso/gesundheit/gesundheitsschutz/badegewaesser/badegewaesserueberwachung/ <br>
https://wasserportal01.stadt-berlin.de/erlaeuterungen.php

### Data into air quality datasets:

| Parameter | Description | Type |
|---|---|---|
| datetime | date/time of the measurement | datetime64[us, UTC] |
| station | station ID | str |
| core | pollutant category | str |
| component | specific component measured | str |
| period | period measured | str |
| value | amount of the pollutant registered | float64 |
| station_name | name of the station | str | #engineered
| station_type | type of station | str | #engineered

Pollutant concentrations  are expressed in µg/m³ (micrograms per cubic metre). I will mostly focus on Nitrogen dioxide (no2), Ozone (o3), pm10 and pm 2.5.

Details on air quality index can be found here: https://luftdaten.berlin.de/lqi/info


### Energy consumption datasets

This dataset contains total consumption in kWh for the city of Berlin every 15 minutes, data is available from 2020 until 2025.

| Parameter | Description | Type |
|---|---|---|
| Datum | day of reported value | str |
| Zeit | specific quarter of reported value | str |
| load_kw | consumption reported in kWh | str | #engineered

96 invalid timestamps: I excluded them from time-based analysis	because the dates were marked as #BEZUG and it's not possible to assign measurements to other dates (these records were found on the original dataset between 01.05.2025 00:00 and 01.05.2025 00:15)
1 Jan (95 records):	Flagged as incomplete as there was one fewer record than expected
31 Dec (1 record): Excluded from daily analysis, there is insufficient daily coverage (only 15 minutes)

### LOR dataset
Lebensweltlich orientierte Räume (life-world-oriented spaces). It is Berlin's official spatial classification system. I am currently using the Bezirksregionen (BZR) level, which shows the district regions of the city, 143 in total

| Column | Data type | Description |
|---|---|---|
| `bzr_id` | Int64 | Unique identifier of the Bezirksregion (BZR), the middle level of Berlin's LOR spatial hierarchy. |
| `bzr_name` | String | Name of the Bezirksregion. |
| `pgr_id` | Int64 | Identifier of the Prognoseraum (PGR), the larger planning area containing the Bezirksregion. |
| `pgr_name` | String | Name of the Prognoseraum. |
| `bez` | String | Name or identifier of the Berlin administrative district (Bezirk) to which the Bezirksregion belongs. |
| `finhalt` | Float64 | Area-related value (`Flächeninhalt`) for the spatial unit. The unit (e.g. square metres or hectares) should be confirmed in the source metadata. |
| `stand` | String | Reference date or status information associated with the spatial dataset. The exact meaning should be confirmed from the source metadata. |


### Satellite/map data

LOR system Berlin explanation: https://www.berlin.de/sen/stadt/stadtdaten/stadtwissen/sozialraumorientierte-planungsgrundlagen/lebensweltlich-orientierte-raeume/

#### Urban Atlas green areas
Showing land cover and land use for the city of berlin

| Column | Data type | Description |
|---|---|---|
| `country` | String | Two-letter country code identifying the country of the Functional Urban Area (e.g. DE). |
| `fua_name` | String | Name of the Functional Urban Area. |
| `fua_code` | String | Identifier of the Functional Urban Area. |
| `code_2021` | String | Official Urban Atlas classification code assigned to each mapped polygon for the 2021 reference year. |
| `class_2021` | String | Descriptive name of the land-cover or land-use category corresponding to `code_2021`. |
| `prod_date` | String | Production date of the dataset, expressed as year and month. |
| `identifier` | String | Unique identifier assigned to each mapped polygon feature. |
| `perimeter` | Float64 | Perimeter of the polygon, expressed in metres. |
| `area` | Float64 | Area of the polygon, expressed in square metres. |
| `comment` | Object | Additional information or remarks associated with the mapped feature, including possible exceptions to the Minimum Mapping Unit. |
| `geometry` | Geometry | Polygon geometry representing the spatial boundaries of the mapped land-cover or land-use feature. |


#### Terrain imperviousness
showing the degree of soil sealing (artificial surface coverage) across Berlin, mapping out exactly where the natural ground has been paved over by human infrastructure

| Attribute | Data type | Description |
|---|---|---|
| `pixel_value` | UInt8 | Imperviousness density value for each 10 × 10 m pixel, expressed as a percentage. Values range from 0 (non-impervious) to 100 (100% impervious). |
| `geometry` | Raster grid | Spatial location and extent of each raster pixel, referenced to EPSG:3035. |


#### Tree cover density
Represents the Tree Cover Density by Berlin neighbourhood

| Attribute | Data type | Description |
|---|---|---|
| `pixel_value` | UInt8 | Tree Cover Density value for each 10 × 10 m pixel, representing the percentage of ground area covered by the vertical projection of tree canopy. Values range from 0 to 100. |
| `geometry` | Raster grid | Spatial location and extent of each raster pixel, referenced to EPSG:3035. |

### Berlin Population (year 2025)

## 1. Time and geographic identifiers

| Column | Data type | Description |
|---|---|---|
| `ZEIT` | String / integer | Reference period in YYYYMM format. `202512` represents December 2025. |
| `RAUMID` | String | Unique geographic identifier for the respective LOR planning area (PLR). |
| `BEZ` | String | Identifier of the Berlin administrative district (*Bezirk*). |
| `PGR` | String | Identifier of the forecast area (*Prognoseraum*). |
| `BZR` | String | Identifier of the neighbourhood region (*Bezirksregion*). |
| `PLR` | String | Identifier of the planning area (*Planungsraum*). |
| `BEZPGR` | String | Combined identifier for the administrative district and forecast area. |

Geographic identifiers are stored as strings to preserve leading zeros.

## 2. Total population and population by sex

| Column | Data type | Description |
|---|---|---|
| `E_E` | Integer | Total number of registered residents in the planning area. |
| `E_EM` | Integer | Number of registered male residents. |
| `E_EW` | Integer | Number of registered female residents. |

For complete records, `E_EM` + `E_EW` = `E_E`.

## 3. Population by detailed age groups

All fields below represent the number of registered residents within the specified age interval. The upper age boundary is exclusive.

| Column | Data type | Description |
|---|---|---|
| `E_E00_01` | Integer | Residents aged 0 to under 1 year. |
| `E_E01_02` | Integer | Residents aged 1 to under 2 years. |
| `E_E02_03` | Integer | Residents aged 2 to under 3 years. |
| `E_E03_05` | Integer | Residents aged 3 to under 5 years. |
| `E_E05_06` | Integer | Residents aged 5 to under 6 years. |
| `E_E06_07` | Integer | Residents aged 6 to under 7 years. |
| `E_E07_08` | Integer | Residents aged 7 to under 8 years. |
| `E_E08_10` | Integer | Residents aged 8 to under 10 years. |
| `E_E10_12` | Integer | Residents aged 10 to under 12 years. |
| `E_E12_14` | Integer | Residents aged 12 to under 14 years. |
| `E_E14_15` | Integer | Residents aged 14 to under 15 years. |
| `E_E15_18` | Integer | Residents aged 15 to under 18 years. |
| `E_E18_21` | Integer | Residents aged 18 to under 21 years. |
| `E_E21_25` | Integer | Residents aged 21 to under 25 years. |
| `E_E25_27` | Integer | Residents aged 25 to under 27 years. |
| `E_E27_30` | Integer | Residents aged 27 to under 30 years. |
| `E_E30_35` | Integer | Residents aged 30 to under 35 years. |
| `E_E35_40` | Integer | Residents aged 35 to under 40 years. |
| `E_E40_45` | Integer | Residents aged 40 to under 45 years. |
| `E_E45_50` | Integer | Residents aged 45 to under 50 years. |
| `E_E50_55` | Integer | Residents aged 50 to under 55 years. |
| `E_E55_60` | Integer | Residents aged 55 to under 60 years. |
| `E_E60_63` | Integer | Residents aged 60 to under 63 years. |
| `E_E63_65` | Integer | Residents aged 63 to under 65 years. |
| `E_E65_67` | Integer | Residents aged 65 to under 67 years. |
| `E_E67_70` | Integer | Residents aged 67 to under 70 years. |
| `E_E70_75` | Integer | Residents aged 70 to under 75 years. |
| `E_E75_80` | Integer | Residents aged 75 to under 80 years. |
| `E_E80_85` | Integer | Residents aged 80 to under 85 years. |
| `E_E85_90` | Integer | Residents aged 85 to under 90 years. |
| `E_E90_95` | Integer | Residents aged 90 to under 95 years. |
| `E_E95_110` | Integer | Residents aged 95 to under 110 years. |

## 4. Population by aggregated age groups

These columns provide broader age categories derived from the detailed age distribution.

| Column | Data type | Description |
|---|---|---|
| `E_EU1` | Integer | Residents aged under 1 year. |
| `E_E1U6` | Integer | Residents aged 1 to under 6 years. |
| `E_E6U15` | Integer | Residents aged 6 to under 15 years. |
| `E_E15U18` | Integer | Residents aged 15 to under 18 years. |
| `E_E18U25` | Integer | Residents aged 18 to under 25 years. |
| `E_E25U55` | Integer | Residents aged 25 to under 55 years. |
| `E_E55U65` | Integer | Residents aged 55 to under 65 years. |
| `E_E65U80` | Integer | Residents aged 65 to under 80 years. |
| `E_E80U110` | Integer | Residents aged 80 to under 110 years. |

## 5. Data quality and processing notes

- The original dataset contains 542 planning-area records.
- Population values are missing for two records: `RAUMID` 03400831 and 06200418.
- These missing values were retained as `NaN` rather than replaced with zero.
- For the 540 complete records, male and female population counts reconcile with the total population.
- The detailed age-group counts also reconcile with the total population for complete records.
- Geographic identifiers were treated as strings to preserve their original formatting.
- The dataset represents a population register snapshot at 31 December 2025, not a continuous population estimate throughout the year.

## 6. Source

Amt für Statistik Berlin-Brandenburg. *Einwohnerinnen und Einwohner in Berlin in LOR-Planungsräumen am 31.12.2025.
