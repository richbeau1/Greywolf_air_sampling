# Greywolf Air Sampling

## Project description

Analysis of paired indoor and outdoor PM2.5 measurements collected using GreyWolf particle monitors as part of PhD research at the University of Sheffield.

The sampling investigates short-term relationships between indoor and outdoor PM2.5 concentrations in UK school environments.

## Data collection

Paired GreyWolf instruments were operated indoors and outdoors during occupied school days.

Measurements were recorded at one-minute intervals.

The current dataset contains:

- School 1: 6–8 July 2026
- School 2: 13–15 July 2026

## Data

Raw GreyWolf exports are stored locally in:

`data/raw/Greywolf_Data/`

Only the particulate-mass files are currently used for PM2.5 analysis.

The PM2.5 variable is the GreyWolf `2.5µm µg/m3` measurement.

Raw data are excluded from Git and are not stored in this repository.

## Data processing

`Greywolf_air_sampling_analysis.Rmd` contains the main workflow.

Current processing includes:

1. Identification of indoor and outdoor particulate-mass files.
2. Extraction of PM2.5 concentrations.
3. Conversion of timestamps to R date-time format.
4. Matching indoor and outdoor observations by school and minute.
5. Calculation of:
   - indoor PM2.5
   - outdoor PM2.5
   - indoor minus outdoor PM2.5
   - indoor/outdoor (I/O) ratio
6. Daily summary statistics.
7. Indoor–outdoor correlation and linear regression.
8. Time-series visualisation using `openair`.

## Project structure

- `Greywolf_air_sampling_analysis.Rmd` — main analysis
- `Greywolf_air_sampling.Rproj` — RStudio project
- `data/raw/` — original GreyWolf data (excluded from Git)
- `renv.lock` — reproducible R package environment
- `README.md` — project documentation

## Software

Analysis is conducted in R and RStudio.

Package dependencies are managed using `renv`.

To restore the project package environment:

`renv::restore()`

`openair` is used where appropriate for air-pollution analysis and visualisation.

## Reproducibility

Raw data should remain unchanged.

All cleaning, matching, derivation and statistical analysis should be performed programmatically from the original files using the R Markdown workflow.

This README should be updated when additional schools, sampling campaigns, datasets or analytical procedures are added.