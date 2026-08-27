# GreyWolf Air Sampling

## Project description

Analysis of paired indoor and outdoor PM₂.₅ measurements collected using GreyWolf particle monitors 
at two primary schools in Sheffield as part of PhD research at the University of Sheffield.

The analysis examines short-term indoor–outdoor PM₂.₅ relationships, attenuation of outdoor PM₂.₅ 
indoors, indoor particle events, and the influence of ambient PM₂.₅ and meteorological conditions.

## Study sites

Two primary schools in Sheffield participated in the study. School identities are anonymised 
throughout the repository and analysis.

- **School 1** — sampled 6–8 July 2026
- **School 2** — sampled 13–15 July 2026

## GreyWolf measurements

Paired indoor and outdoor GreyWolf measurements were collected at approximately one-minute 
resolution during each sampling period.

The analysis uses the GreyWolf PM₂.₅ mass concentration measurement.

Raw monitoring data are stored locally under:

`data/raw/`

Raw data are excluded from Git and are not included in the repository.

## External ambient PM₂.₅

Hourly ambient PM₂.₅ observations are obtained from the DEFRA Automatic Urban and Rural 
Network (AURN) Sheffield Devonshire Green urban-background monitoring station.

These observations provide an independent measure of wider ambient PM₂.₅ conditions 
during the school sampling periods.

## Meteorology

Hourly meteorological observations are obtained from the Sheffield Airviro Athletic Stadium meteorological station.

Variables incorporated into the analysis are:

- air temperature
- atmospheric pressure
- wind speed
- wind direction
- rainfall

The 10 m wind measurements are used where observations are available at multiple heights.

## Master analysis dataset

The definitive analysis-ready R object is:

`greywolf_master`

This is the source dataset used for all subsequent analyses.

It contains:

- minute-level indoor GreyWolf PM₂.₅
- minute-level outdoor GreyWolf PM₂.₅
- indoor–outdoor PM₂.₅ difference
- indoor/outdoor PM₂.₅ ratio
- hourly Devonshire Green ambient PM₂.₅
- hourly Athletic Stadium air temperature
- hourly atmospheric pressure
- hourly wind speed
- hourly wind direction
- hourly rainfall

Hourly external observations are assigned to the corresponding GreyWolf minute observations 
while retaining the original minute-level GreyWolf measurements.

The processed master dataset is saved locally as:

`data/processed/greywolf_master.rds`

The processed dataset is excluded from Git because it can be reproduced from the original 
data using the analysis workflow.

## Analysis workflow

The principal analysis is contained in:

`Greywolf_air_sampling_analysis.Rmd`

The current workflow includes:

1. Import and identification of GreyWolf particulate-mass files.
2. Extraction of indoor and outdoor PM₂.₅.
3. Minute-level temporal matching of paired indoor and outdoor measurements.
4. Sampling coverage checks.
5. Daily indoor and outdoor descriptive statistics.
6. Indoor/outdoor PM₂.₅ ratios and concentration differences.
7. Minute-level indoor–outdoor correlations and regression.
8. Openair time-series visualisation.
9. Openair indoor–outdoor scatter plots.
10. Aggregation to 15-minute mean concentrations using `openair::timeAverage()`.
11. Comparison of indoor–outdoor relationships using 15-minute means.
12. Integration of Devonshire Green ambient PM₂.₅.
13. Integration of Athletic Stadium meteorological observations.

## Project structure

- `Greywolf_air_sampling_analysis.Rmd` — main reproducible analysis
- `Greywolf_air_sampling.Rproj` — RStudio project
- `README.md` — project documentation
- `renv.lock` — record of the R package environment
- `data/raw/` — original monitoring and external data; excluded from Git
- `data/processed/` — generated analysis-ready datasets; excluded from Git

## Reproducibility

Analysis is performed in R/RStudio, using `openair` where appropriate for air-pollution 
analysis and visualisation.

Package dependencies are managed using `renv`.

The package environment can be restored using:

`renv::restore()`

Raw monitoring data should remain unchanged. Data cleaning, temporal matching, aggregation and 
statistical analyses are performed programmatically within the R workflow.

School identities must remain anonymised in all repository files, code, 
documentation, figures and outputs.