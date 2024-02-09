# Mexican Fisheries Data

This badge shows the DOI for the latest release --> [![DOI](https://zenodo.org/badge/362593818.svg)](https://zenodo.org/badge/latestdoi/{362593818})

This repository contains the code to clean and maintain what I call the `Mexican fisheries data` set. This data set contains tables on Mexico's Vessel Monitoring System (VMS) tracking data, a vessel registry, landings data, and some other things. Data themselves are NOT archived in the repository (due to GitHub's size constraints). But they are available upon request. Please submit an issue or send me an email. I am more than happy to share any and all these data and see them put to a good use. If you want to come up with a way of automating the delivery of the data, please reach out to me. I simply don't have the time.

There is a [Makefile](Makefile) outlining dependencies and order of operations, and the DAG is shown here:

![](workflow.png)

## Mexican VMS data (2007 - 2023 [partial])

These data are collected and curated by Mexico's [`SISMEP`](https://www.gob.mx/conapesca/acciones-y-programas/sistema-de-monitoreo-satelital-de-embarcaciones-pesqueras) (Sistema de Monitoreo Satelital de Embarcaciones Pesqueras). It reports the geolocation and timestamp of mexican fishing vessels that comply with [Mexico's fisheries regulation](https://www.dof.gob.mx/nota_detalle.php?codigo=5399371&fecha=03/07/2015#gsc.tab=0) on the matter. Simply put, vessels larger than 10m in length overall, with an onboard engine, and with a roof must carry a tansponder.

### Raw sources

- [Datos abiertos](https://datos.gob.mx/busca/dataset/localizacion-y-monitoreo-satelital-de-embarcaciones-pesqueras)

### "Clean" data vailability, with two different levels of processing (Email me for access)

- L1 data: On Google Cloud storage at: `gs://mex_fisheries/MEX_VMS/*` with monthly `*.csv` files.
- L1 and L2 data: On Google BigQuery at: `mex-fisheries.mex_vms.mex_vms_*` as a partitioned table (by year) and some level of processing

_NOTE: For details on the data cleaning, next steps, and know issues, see the dedicated [README](/scripts/vms). File may not be up to date_

## Vessel registry

### Raw data sources

- Data set shared by [CausaNatura](www.causanatura.org)

### "Clean" data availability

- On Google BigQuery at: `mex-fisheries.mex_vms.svessel_info_v_*`

## Landings data

### Raw data sources

- CONAPESCA Avisos (2000-2019) (No link, obtaiend offline)
- [CONAPESCA_apertura (2018-2023)](https://conapesca.gob.mx/wb/cona/avisos_arribo_cosecha_produccion)
- [Datos_abiertos](https://datos.gob.mx/busca/dataset/produccion-pesquera)

### "[Clean](data/mex_landings/clean)" data availability

#### Data by economic unit RNPA
- [annual](data/mex_landings/clean/mex_annual_landings_by_eu.rds)
- [monthly](data/mex_landings/clean/mex_monthly_landings_by_eu.rds)

#### Data by vessel RNPA
- [annual](data/mex_landings/clean/mex_annual_landings_by_vessel.rds)
- [monthly](data/mex_landings/clean/mex_monthly_landings_by_vessel.rds)

## Subsidy data

### Sources

### Availability

## Spatial features

### Sources

- [Sea: Global Oceans and Seas](https://www.marineregions.org/sources.php)
- [EEZ: Marine and land zones: the union of world country boundaries and EEZ's](https://www.marineregions.org/sources.php)
- [Distance from shore](https://gmed.auckland.ac.nz/download.html)
- [Distance from port](https://gmed.auckland.ac.nz/download.html)
- [Depth](https://gmed.auckland.ac.nz/download.html)
