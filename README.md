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
1) In the WECC loads in CISO, IPCO, NEVP, and PACE are modeled as a whole in TELL but are separated in GridView. To 
create the data for these BAs I used the whole load simulated by TELL and distributed it to the subregions within the 
BA using the annual total load in each subregion to portion out the TELL loads. Those subregions will have different the
same hour-to-hour variability but different magnitudes depending on their total load fractions.
2) In the EIC loads in FMPP, FPL, MISO, PJM, SOCO, SWPP, and TVA are modeled as a whole in TELL but are separated in 
GridView. I used the same technique to subdivide the loads as I did in the original WECC data workflow.
3) TELL does not model BAs in Canada or Mexico. For BAs in those countries (CFE, IESO, TE, NB, NS, CORNWALL, NF, BCHA, 
and AESO) I used the raw time series from the WECC+EIC Gridview file that Kostas passed to me.
4) There are some regions that have no mapping to BAs modeled by TELL. For those regions I used the raw time series from 
the WECC+EIC Gridview file that Kostas passed to me. Those BAs are SETH, SERU, SEHA, IPP-REL, MH, TH_Mead, TH_Malin, 
SPC, TH_PV, OSC, PS, MPW, GLH, CPLW, YAD, WECC, and WBDC-WECC. Many of these regions have 0 loads in the GridView file.