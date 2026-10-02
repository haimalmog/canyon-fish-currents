# Hydrodynamic-model output (not included)

Script 2 (`scripts/02_Model_Mooring_Comparison.Rmd`) uses hourly near-bottom currents
from a hydrodynamic model of the Gulf of Eilat/Aqaba (December 2011 – November 2012),
extracted at the grid cells nearest to the study stations (Table S3 of the article).

These data are not distributed with this repository. They are available from the
authors on reasonable request.

To run Script 2, place the file

```
NearBottomCurrents_DeepStations_2011_2012.csv
```

in this folder. Its columns are: `DateTime` (`dd/mm/yyyy HH:MM`), `Canyon`, `Location`,
`Iteration`, `Station`, `StationLatitude`, `StationLongitude`, `ModelLatitude`,
`ModelLongitude`, `TargetDepth_m`, `BottomDepth_m`, `U_cm_s`, `V_cm_s`, `W_cm_s`,
`Speed_cm_s`, `DirectionTo_deg`.
