# Dataset

## Overview

This directory contains the dataset used for the MSc machine learning project on palm oil waste prediction in Nigeria.

The dataset consists of 732 monthly observations covering the period from January 1964 to December 2024.

## Variables

| Variable | Description |
|---|---|
| Year | Calendar year |
| Month | Month name |
| Month_Number | Numerical month (1–12) |
| Quarter | Calendar quarter (Q1–Q4) |
| FFB_1000MT | Fresh Fruit Bunch production (thousand metric tonnes) |
| EFB_1000MT | Empty Fruit Bunch quantity (thousand metric tonnes) |
| PKS_1000MT | Palm Kernel Shell quantity (thousand metric tonnes) |
| POME_1000MT | Palm Oil Mill Effluent quantity (thousand metric tonnes) |
| Mesocarp_Fibre_1000MT | Mesocarp Fibre quantity (thousand metric tonnes) |
| Avg_Temperature_C | Average temperature (°C) |
| Rainfall_mm | Rainfall (mm) |
| Humidity_pct | Relative humidity (%) |
| Wind_Speed_ms | Wind speed (m/s) |
| Solar_Radiation_Wm2 | Solar radiation (W/m²) |

## Target Variables

Four palm oil waste streams were modelled:

- Empty Fruit Bunches (EFB)
- Palm Kernel Shells (PKS)
- Palm Oil Mill Effluent (POME)
- Mesocarp Fibre (MF)

## Important Data Characteristics

The waste quantities were derived from Fresh Fruit Bunch (FFB) production using established conversion factors:

- EFB: approximately 22% of FFB
- PKS: approximately 6% of FFB
- POME: approximately 65% of FFB
- Mesocarp Fibre: approximately 13% of FFB

Consequently, FFB has a strong deterministic relationship with the target variables. This relationship should be considered when interpreting model performance.

The environmental variables contain repeated monthly climatological profiles for part of the historical period. Therefore, these variables should not be interpreted as independently observed year-specific weather measurements across the entire 1964–2024 period.

## Data Quality

The final dataset contains:

- 732 monthly observations
- 61 complete years
- 14 variables
- No missing values
- No duplicate year-month observations

## Research Use

The dataset was developed for an MSc research project at Cranfield University investigating stacking-based ensemble machine learning for palm oil waste prediction under uncertainty.
