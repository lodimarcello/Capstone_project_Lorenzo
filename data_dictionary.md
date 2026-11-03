
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

I will focus on the following variables: tavg (average daily temperature), tmin-tmax(min/max daily temperature), prcp (daily precipitation), wspd (avg wind speed), pressure (pres_meteostat taken at sea level and pres_dwd taken at station elevation)

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
More info can be found below:

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

I will mostly focus on Nitrogen dioxide (no2), Ozone (o3), pm10 and pm 2.5. I will also check Carbon Monoxide (CO) if enough values are present.

Details on air quality index can be found here: https://luftdaten.berlin.de/lqi/info


### energy consumption datasets

This dataset contains total consumption in kWh for the city of Berlin every 15 minutes, data is available from 2020 until 2025.

| Parameter | Description | Type |
|---|---|---|
| Datum | day of reported value | str |
| Zeit | specific quarter of reported value | str |
| load_kw | consumption reported in kWh | str | #engineered

96 invalid timestamps: I excluded them from time-based analysis	because the dates were marked as #BEZUG and it's not possible to assign measurements to other dates (these records were found on the original dataset between 01.05.2025 00:00 and 01.05.2025 00:15)
1 Jan (95 records):	Flagged as incomplete as there was one fewer record than expected
31 Dec (1 record): Excluded from daily analysis, there is insufficient daily coverage (only 15 minutes)


### Satellite/map data

LOR system Berlin explanation: https://www.berlin.de/sen/stadt/stadtdaten/stadtwissen/sozialraumorientierte-planungsgrundlagen/lebensweltlich-orientierte-raeume/

Urban Atlas green areas 2021

| Parameter | Description |
|---|---|
| bzr_id | Bezirk ID |
| bzr_name | Bezirksregion name |
| bez | Bezirk |
| urban_fabric | Urban areas |
| green_natural | Green areas |
| industrial_commercial | Commercial/industrial areas |
| transport_infrastructure | Infrastructure areas |
| water_wetlands | Water/wetland areas |
| Arable land (annual crops) | Arable land |
| Complex and mixed cultivation patterns | Land with small/diverse agricultural patterns |
| Construction sites | Construction sites |
| Isolated structures | Scattered/low-density buildings |
| Land without current use | Unused land |
| Mineral extraction and dump sites | Mines and dumps |
| Open spaces with little or no vegetation (beaches, dunes, bare rocks, glaciers) | Open land with little or no vegetation |
| Sports and leisure facilities | Sports/leisure facilities |
all values in this dataset are strings