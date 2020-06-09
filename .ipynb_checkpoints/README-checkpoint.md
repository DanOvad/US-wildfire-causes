# Mapping and predicting causes of fires in the USA
**By: Dan Ovadia** \
Date: June 8, 2020
# Read Me
This project is intended to explore a large dataset that has been provided by FPA-FOD for the last 5 years. 
There are 1.88 million fires recorded in the United States from 1992-2017 and we will be exploring the causes, and where these fires mostly happen.
----
## Problem Statement
Predicting or preparing for wildfires has always been challenge. Many catastrophes and natural disasters impact society in many different ways, but the shear speed and unpredictability of how wild fires spread and behave still impacts societies today. \\
In recent years 

## Data
Using data from the US Department of Agriculture, specifically referencing the Spatial wildfire occurrence data for the United States, 1992-2015 (FPA_FOD_20170508) (4th Edition).

This data publication contains a spatial database of wildfires that occurred in the United States from 1992 to 2015. The following core data elements were required for records to be included in this data publication: discovery date, final fire size, and a point location at least as precise as Public Land Survey System (PLSS) section (1-square mile grid). The data were transformed to conform, when possible, to the data standards of the National Wildfire Coordinating Group (NWCG). Basic error-checking was performed and redundant records were identified and removed, to the degree possible. The resulting product, referred to as the Fire Program Analysis fire-occurrence database (FPA FOD), includes 1.88 million geo-referenced wildfire records, representing a total of 140 million acres burned during the 24-year period.

### FPA_FOD Fires Data
| Value | Description |
| :---: | :---: |
| Fires
| FOD_ID
| FPA_ID
| SOURCESYSTEMTYPE
| SOURCESYSTEM
| NWCGREPORTINGAGENCY
| NWCGREPORTINGUNIT_ID
|

### Causes 
| value | Description |
| ----- | ----------- |
| 1 | Lightning |
| 2 | Equipment Use |
| 3 | Smoking |
| 4 | Campfire |
| 5 | Debris Burning |
| 6 | Railroad |
| 7 | Arson |
| 8 | Children |
| 9 | Miscellaneous |
| 10 | Fireworks |
| 11 | Powerline |
| 12 | Structure |
| 13 | Missing/Undefined |

### Fire Sizes
| Value | Description |
| :---: | :---: |
|   A   | Greater than 0 but less than or equal to 0.25 Acres |
|   B   | 0.26 to 9.9 Acres |
|   C   | 10.0 to 99.9 Acres |
|   D   | 100 to 299 Acres |
|   E   | 300 to 999 Acres |
|   F   | 1000 to 4999 Acres |
|   G   | 5000 to 9999 Acres |
|   H   | 10000 to 49999 Acres |
|   I   | 50000 to 99999 Acres |
|   J   | 100000 to 499999 Acres |
|   K   | 500000 to 999999 Acres |
|   L   | 1000000 + Acres |

## Cleaning
Cleaning Dates
Inserting FIPS codes for more accurate mapping (660,000 rows were None)
Removing PR and territories of the US

## Section 1 - Fire Causes

### EDA
### Mapping
### Modeling

## Section 2 - Mapping large fires in the continuous United States

## EDA

## Mapping

## Modeling

## Conclusion

## Next Steps
