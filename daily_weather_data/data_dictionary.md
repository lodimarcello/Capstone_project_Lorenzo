(add the range like number of stations I have data for and date range)
Data contained into meteostat datasets:

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

I will drop the columns snow, wdir, wpgt and tsun


Data contained into DWD datasets:

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

I will drop: qn_3, fx, fm, qn_4, RSK, SDK, SHK_TAG, VPM, PM, TGK

Regarding water quality, data dictionaries can be found here:
https://www.berlin.de/lageso/gesundheit/gesundheitsschutz/badegewaesser/badegewaesserueberwachung/
https://wasserportal01.stadt-berlin.de/erlaeuterungen.php

