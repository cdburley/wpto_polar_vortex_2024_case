# wpto_polar_vortex_2024_case
This repository houses the raw data and processing scripts to create the hourly load time series by 
Balancing Authority for the WPTO polar vortex case. The process starts with the observed EIA-930 demands that were 
previously cleaned for the NAERM RA2.0 project. We subset that data to just the 2024 weather year hourly demands which 
are then scaled to match the 2030 annual total loads data by BA from the WECC 2030 ADS.

## Input Files
The input data needed to recreate this process is stored in the [data](data/) directory.

## Output Files
The output of this processing is stored in the [data](data/) directory.

## Summary Plots
Quick-look plots analyzing the data are stored in the [plots](plots/) directory.

## Notes
1) In the WECC, loads in PG&E, IPCO, NEVP, and PACE are reported as an aggregate value in EIA-930 but are reported in 
separate subregions in the WECC 2030 ADS GridView data. To create the data for these BAs I used the whole load reported 
in EIA-930 and distributed it to the subregions within the BA using the annual total load in each subregion to portion 
out the loads. Those subregions will have different the same hour-to-hour variability but different magnitudes 
depending on their total load fractions.
3) EIA-930 does not include BAs in Canada or Mexico. For BAs in those countries (AESO, BCHA, and CFE) I used the raw 
time series from the WECC 2030 ADS Gridview file.
4) There are some regions that have no mapping to BAs in EIA-930. For those regions I used the raw time series from 
the WECC 2030 ADS Gridview file. Those BAs are TH_Mead, TH_Malin, and TH_PV - all of which have 0 loads in the WECC 
2030 ADS GridView file.