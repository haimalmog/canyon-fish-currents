# Hydrodynamic-model output

`near_bottom_currents_model_2011_2012.csv.gz` – hourly near-bottom currents from a
three-dimensional hydrodynamic model of the Gulf of Eilat/Aqaba (December 2011 –
November 2012), extracted at the model grid cells nearest to the 18 study stations
(100, 200 and 300 m, inside and outside Eilat, Shlomo and Princess Canyons; see
Table S3 of the article). The file is a gzip-compressed CSV (8,760 hourly rows per
station); R (`readr::read_csv`) reads it directly, and it can be opened with any
unzip tool.

| Column | Description |
|---|---|
| `DateTime` | date and time, `dd/mm/yyyy HH:MM` (UTC) |
| `Canyon`, `Location` | canyon and position (`In` / `Out`) |
| `Iteration` | model time step |
| `Station` | station name |
| `StationLatitude`, `StationLongitude` | target station position (decimal degrees) |
| `ModelLatitude`, `ModelLongitude` | centre of the model grid cell (decimal degrees) |
| `TargetDepth_m` | target depth of the station (m) |
| `BottomDepth_m` | bottom depth of the model grid cell (m) |
| `U_cm_s`, `V_cm_s`, `W_cm_s` | eastward, northward and vertical velocity (cm s⁻¹) |
| `Speed_cm_s` | horizontal current speed (cm s⁻¹) |
| `DirectionTo_deg` | direction toward which the current flows (degrees from north) |

The 100-m stations are named after the mooring sites (e.g. `Eilat Canyon - inside`;
`Solomon` = Shlomo Canyon).
