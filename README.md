# Data

All files are comma-separated (CSV, UTF-8). Times are local time (Asia/Jerusalem).
Missing values are empty cells or `na`.

## `moorings/` – current meters and temperature loggers

Nine near-bottom moorings were deployed in 2026 (see Table S1 of the article for
coordinates and dates):

| Canyon | Station | Bottom depth | Files |
|---|---|---|---|
| Eilat | inside (`in`) / outside (`out`) the canyon | 100 m | `eilat_100m_{in,out}_{current,temperature}.csv` |
| Princess | inside / outside | 100 m | `princess_100m_{in,out}_{current,temperature}.csv` |
| Shlomo | inside / outside | 100 m | `shlomo_100m_{in,out}_{current,temperature}.csv` |
| Shlomo | inside / outside | 200 m | `shlomo_200m_{in,out}_{current,temperature}.csv` |
| Shlomo | continental shelf | 80 m | `shlomo_80m_shelf_{current,temperature}.csv` |

The records include the periods before and after the instruments were on the seabed;
the scripts remove these (first and last 3 h of every record, and the time windows
defined in each script).

### `*_current.csv` – tilt current meter (1 m above the seabed, 10-min interval)

| Column | Description |
|---|---|
| `ISO 8601 Time` | date and time (ISO 8601) |
| `Speed (cm/s)` | current speed |
| `Heading (degrees)` | direction toward which the current flows (degrees from north) |
| `Velocity-N (cm/s)` | northward velocity component (v) |
| `Velocity-E (cm/s)` | eastward velocity component (u) |

### `*_temperature.csv` – temperature loggers on the mooring line (10-min interval)

| Column | Description |
|---|---|
| `time` | date and time (ISO 8601 for Shlomo; `dd/mm/yyyy HH:MM` for Eilat and Princess) |
| `temp - depth D` | temperature (°C) at water depth D (m). With bottom depth B: D = B is the seabed logger, B − 1, B − 3 and B − 5 are 1, 3 and 5 m above the seabed. The Eilat and Princess files also contain a logger at 85 m (15 m above the seabed), which is not used in the analyses |
| `Station` | `In` / `Out` (inside / outside the canyon) |
| `Bottom_depth`, `bottom_depth` | bottom depth of the mooring (m) (Shlomo files) |

`shlomo_80m_shelf_temperature.csv` has a single logger 1 m above the seabed
(`ISO 8601 Time`, `Temperature (C)`).

## `bruvs/` – baited remote underwater video systems

### `bruvs_deployments.csv` – one row per deployment (56 deployments)

| Column | Description |
|---|---|
| `OpCode` | deployment code (links to `bruvs_maxn.csv`) |
| `sea`, `location` | sea (`red`) and coastal sector |
| `Canyon` | Eilat, Shlomo or Princess |
| `Canyon_Location` | `In` (inside the canyon) or `Out` (adjacent open slope) |
| `lat_y`, `lon_x` | position (decimal degrees, WGS84) |
| `date`, `dep_time` | deployment date (`dd/mm/yyyy`) and time |
| `system_id` | BRUVS unit |
| `depth` | bottom depth (m) |
| `temperature` | near-bottom temperature during the deployment (°C) |
| `seabed`, `seabed_form` | seabed description and form (consolidated / unconsolidated / both) |
| `Substrate` | substrate class used in the analyses: `Hard`, `Mixed` or `Soft` |
| `complexity` | habitat-complexity score (0–4) |

### `bruvs_maxn.csv` – one row per taxon per deployment

| Column | Description |
|---|---|
| `OpCode` | deployment code |
| `Family`, `Species` | taxon (empty `Species`: not identified to species level, or no fish recorded) |
| `MaxN` | maximum number of individuals of the taxon seen in a single video frame |
| `Depth`, `temperature`, `Canyon`, `Location` | copied from the deployment table |

## `model/` – hydrodynamic-model output

Hourly near-bottom currents from the hydrodynamic model at the 18 study stations
(December 2011 – November 2012); see `model/README.md`.
