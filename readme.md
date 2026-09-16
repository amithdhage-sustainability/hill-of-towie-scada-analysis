# Hill of Towie SCADA Data Analysis

This repository contains exploratory data analysis of SCADA data from the
Hill of Towie wind farm.

The work forms part of a broader research project on wind farm layout
optimization, with particular emphasis on accurately representing turbine
inflow conditions and wake effects.

## Dataset

The analysis uses 10-minute SCADA data from the Hill of Towie wind farm.

For the initial analysis, data from January 2025 is used. The dataset contains
measurements from 21 wind turbines, with all turbines stored in the same
monthly SCADA file.

The principal variable currently used is:

- `wtc_AcWindSp_mean` — 10-minute mean wind speed from the active wind-speed
  sensor selected by the turbine controller.

The raw SCADA data is not included in this repository.

## January 2025 Analysis

The January dataset was cleaned to retain the following variables:

- `TimeStamp`
- `StationId`
- `wtc_AcWindSp_mean`

The following data-quality checks were performed:

- Confirmed 21 wind turbines
- Confirmed 4,464 ten-minute observations per turbine
- Confirmed continuous 10-minute timestamp spacing
- Removed the month-boundary record corresponding to the previous month
- Verified that no turbine-timestamp combinations are duplicated
- Verified that the retained variables contain no missing values

The cleaned January dataset therefore contains:

- 21 turbines
- 4,464 observations per turbine
- 93,744 total observations

## Exploratory Analysis

Initial exploratory analysis includes:

- Descriptive statistics of wind speed
- Wind-speed time-series visualization
- Wind-speed frequency distribution
- Comparison of mean wind speed across all 21 turbines

The January farm-wide mean wind speed is approximately 7.24 m/s, although
clear differences exist between individual turbines.

## Wind Power

The kinetic power available in the wind passing through the turbine rotor area
can be estimated using:

P = 0.5 × rho × A × U³

where:

- `rho` is air density
- `A` is rotor swept area
- `U` is the measured wind speed

This represents available wind power and should not be interpreted as actual
electrical turbine output. Future analysis will use turbine power
characteristics or measured SCADA power for power-production assessment.

## Future Work

The same analysis workflow will be extended to the remaining months of 2025.

Subsequent work will include:

- Full-year wind-speed analysis
- Wind-direction analysis
- Turbine spatial relationships
- Identification of wake-affected operating conditions
- Comparison between measured turbine inflow and analytical wake-model
  predictions
- Wind farm energy-production modelling
- Integration with wind farm layout optimization

## Tools

- Python
- pandas
- NumPy
- Matplotlib
- Google Colab
