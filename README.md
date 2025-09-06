# E-HYPE-Tools - Discharge-projections-from-SMHI
The swedish institute SMHI products Hydrology related climate change impact indicators, wich includes discharge, worldwide and Europe.

### E-HYPE (SMHI) - Hydrology Discharge Projections via Climat Data Store - Multi Models  MONTHLY INDICATORS Analysis 
 European Hydrological Predictions for the Environment - Geographic Europe only (--> E-HYPE)

LIMITATIONS:
- This dataset on Climate Data Store is the obsolete CMIP5 version of the swedish institut SMHI, which is preparing a CMIP6 version that will likely be chargeable like all other SMHI products.
- This code only processes the FLOW m3/s INDICATOR (and not the % indicator as a relative to the histroical reference, which does not allow comparison with available measurements).
- Currently, the code processes a single node (but all climate models and all 8 hydrological models).
- This is the interannual average over three periods: historical (1971-2000, coded as 1971), 2041-2070 (coded as ), 2071-2100 (coded as ).
- PROBLEM WITH THIS INDICATOR MONTHLY VERSION: Comparing the reference period 1971-2000 with observations is not necessarily relevant if the measurement period covers very different years:
    - it is necessary to reason in terms of the percentage drop to be applied to the observed data to avoid modeling bias (the modeled flow rate can be very different from the actual flow rate, even when averaged over an identical period)
    - PROBLEM WITH THE DAILY VERSION: if the measured period covers years that are too different from the reference period of INDICATOR MONTHLY (1971-2000), the theoretical alternative would be to use the DAILY version, which allows for the interannual average over a period identical to the observed data. This poses a problem because, as explained below, the prohibitive volume of data complicates this solution (not to mention the more complex coding problem).

------------------------------------
- data (Copernicus Climate Data Store) : https://cds.climate.copernicus.eu/datasets/sis-hydrology-variables-derived-projections?tab=overview
- Doc : https://confluence.ecmwf.int/pages/viewpage.action?pageId=283549812
- Sub Basins map online: https://hypeweb.smhi.se/explore-water/historical-data/europe-time-series/ 
- Sub Basins ID : https://zenodo.org/records/581451

"29 Jan 2025
This dataset is no longer supported by the data providers. Data and documentation are provided as is. Users are encouraged to use our Forum to raise any item of discussion with respect to this dataset."

PRODUCT FEATURES:
- See the personal description document
- Each scenario includes 64 different modeling scenarios (8x8 combination of GCM_RCM_member)
- Each file contains a SINGLE combination of 8 CLIMATE MODELING ANALYSES (GCM_RCM_member) for the same scenario, including the 8 HYDRO models, for the entire geographical area of ​​Europe.

MULTI-MODEL APPROACH & File Size Constraints
- Since results can vary depending on the modeling scenario, a single modeling combination can be misleading (a file contains a single climate combination of 8, including the 8 HYDRO models, i.e., 8 combinations out of 64).
- To conduct a study, it is scientifically necessary to have a multi-model approach, i.e., several files representing different GCM_RCM_member_HYDRO combinations.

A multi-model approach is possible with the MONTHLY INTERANNUAL THROUGHPUT INDICATOR, but in practice it's unthinkable with the DAILY THROUGHPUT INDICATORS.
- Indeed, each huge daily zip file (out of 8) represents 90 GB, even unzipped! That's almost 720 GB for the entire dataset --> Retrieval time for each huge zip file represents more than a day!
- Query time is prohibitive, and even random, as the query can fail after several hours and must be rerun to succeed.
- Unzipping time of 2 or 3 hours
- Requires storage media capable of supporting the volume (x2 if you want to keep the zip archives for security) --> additional problem of network or internet/Wi-Fi connection interruption.

