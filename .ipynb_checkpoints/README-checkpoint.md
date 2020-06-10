# Mapping and predicting causes of fires in the USA
**By: Dan Ovadia** \
Date: June 8, 2020
# Read Me

This project is intended to explore a large dataset that has been provided by FPA-FOD for the last 5 years. 
There are 1.88 million fires recorded in the United States from 1992-2017 and we will be exploring the causes, and where these fires mostly happen.

----
## Problem Statement
Predicting or preparing for wildfires has always been challenging. Many catastrophes and natural disasters impact society in many different ways, but the shear speed and unpredictability of how wild fires spread and behave still impacts societies today.

In the last five years federal agencies have taken it upon themselves to aggregate and examine fire databases to cummulate an archive of fires, fire causes, and fire sizes to better understand the impacts that fires have had on society as a whole. This data was first made public in 2017, and provides many avenues for investigating and assessing fire risk in the United States. 

Given recent increases in wild fire incidents and fire severity in California and the Pacific North West, catastrophe insurance companies and risk modeling companies have begun to reassess their methodology for pricing fire risk. Since insurance rates and regional governments tend to drive regulation and fire protection methods, assessing the data available is the first step toward building a more resilient society towards wild fire risks. 

## Objective
The intent of this project is to explore the data and to assess the cause of a fire based on date, location, owner code of the land, and reporting agency. These are first steps toward exploring fire risk in the United States and to assess vulnerability of fire hazard in various counties.

## Data
Using data from the US Department of Agriculture, specifically referencing the Spatial wildfire occurrence data for the United States, 1992-2015 (FPA_FOD_20170508) (4th Edition).

This data publication contains a spatial database of wildfires that occurred in the United States from 1992 to 2015. The following core data elements were required for records to be included in this data publication: discovery date, final fire size, and a point location at least as precise as Public Land Survey System (PLSS) section (1-square mile grid). The data were transformed to conform, when possible, to the data standards of the National Wildfire Coordinating Group (NWCG). Basic error-checking was performed and redundant records were identified and removed, to the degree possible. The resulting product, referred to as the Fire Program Analysis fire-occurrence database (FPA FOD), includes 1.88 million geo-referenced wildfire records, representing a total of 140 million acres burned during the 24-year period. [Source: United States Department of Agriculture Forest Service](https://www.fs.usda.gov/rds/archive/catalog/RDS-2013-0009.4)



## Cleaning
The data do not provide a lot of contextual details into each fire. FIPS codes were missing for a third of the data. In order to thoroughly map out the data by county and assess risk by county, cleaning the FIPS codes by county was essential. This was done by downloading polygons of US counties and checking which county each point of fire ignition belongs to.

## Exploratory Data Analysis
### Section 1 - Fire Causes
First lets explore the spread of causes by state.

### Causes 
The data provide 13 statistical causes ranging from natural causes to malicious causes.

| STAT_CAUSE_CODE | STAT_CAUSE_DESCR |
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

First lets look at the spread of causes over all 1.8 million fire ignitions. 
   <img src="./plots/dist_by_cause.png" alt="Example" width="800" height="">
   
Here we see that Debris Burning, Arson, Miscellaneous and Lightning are the leading causes of fire occurrence by count. 
   
   <img src="./plots/area_by_cause.png" alt="Example" width="800" height="">
   
Yet when looking at fire size by cause, we see that lightning is by far the leader in causing large fires that burn large areas. This makes sense because those fires likely take time to discover and get under control. Fires that are caused by human causes are likely reported earlier and easier to access. They are also likely considered higher priority since they may threaten homes and buildings.
   
Next we will break out the distribution of fire counts and burned area by state and cause to see what differences exist in different states. 

   <img src="./plots/dist_count_by_cause_state.png" alt="Example" width="1200" height="">
   
Here we see that Lightining is still a leading cause of fire occurrence in states that are primarily threatened by large wildfires. States such as Alaska, Arizona, California, Colorado, Idaho, Montana, New Mexio, Nevada, etc. 
   
   <img src="./plots/prop_count_by_cause_state.png" alt="Example" width="1200" height="">
   
Looking at burned area by state and cause we see that lightning leads the cause of large areas being burned. Alaska is a huge outlier, likely due to the huge area that Alaska covers that are unihabited. But we also see Idaho, Montana, New Mexio, Nevada, and Oregon having large fires caused by lightning. 

Also california is a bit more unique. California is heavily populated, even it's rural areas are more populated than other states unihabited areas such as Alaska, and it seems that California has a wide range of causes that lead to large fires. This explains the unique threat that wildfires create for California, as fires plague the state in all areas from rural to urban regions.
   
   <img src="./plots/dist_area_by_cause_state.png" alt="Example" width="1200" height="">
   
Here we have another graph showing proportion of burned area by cause and state, and we see that of the states that had high burn areas in the previous graph, CA is unique in their distribution of causes.
   
   <img src="./plots/prop_area_by_cause_state.png" alt="Example" width="1200" height="">


### Section 2 - Fire Classes

Next we will take a look at fire sizes by class.

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


   <img src="./plots/dist_by_class.png" alt="Example" width="800" height="">
   
Here we see that class A and class B are the most common fire occurrences, which makes sense since these are generally smaller fires that become under control fairly quickly. Also these fires likely started on days that did not have conducive weather to spread a fire. 

   <img src="./plots/area_by_class.png" alt="Example" width="800" height="">
Of course when we look at burned area by class, we see that class G by far burns the most area, even though they are the rarest of fires. These fires likely started on days that had severe fire weather with high winds and dry brush in its path, leading to larger out of control fires. 
   
   <img src="./plots/dist_count_class_state.png" alt="Example" width="1200" height="">
   
The above graph shows count of fires by class. Here we see that California is leading with the number of fires, with Texas, and Florida following behind. It's surprising to see that Alaska is not one of the states leading with the most count of fires. Yet with the high number of human caused fires, Alaskas small population likely leads to a smaller number of fires. While California, Florida, Texas, and Georgia have both high populations and large areas that are susceptible to fires.
   
   <img src="./plots/prop_count_class_state.png" alt="Example" width="1200" height=""> 
   
   <img src="./plots/dist_area_by_class_state.png" alt="Example" width="1200" height="">
   
Now looking at burn area by fire size, Alaska is again the clear leader in this pack since G fires burn huge swaths of Alaska regularly. California and Idaho then come in second and third due to their huge territories that are susceptible to large fires and have terrains that make it difficult to control. 
   
   <img src="./plots/prop_area_by_class_state.png" alt="Example" width="1200" height="">

## Mapping

In order to explore how fire counts by state change over time, I created an interactive scatter_mapbox using Plotly to see how fire distribution changes year-by-year. Surprisingly we see that areas that fire concentrations changes year over year. The first graph looks at states and counts of fires, while the second graph looks at points of origin and fire size. 

![](./states-count-by-year.gif)

Below we see concentrations that shift throughout the country. Sometimes the southwest is covered with large fires, sometimes it's the Pacific Northwest, and othertimes Alaska is littered with large fires. This seasonality is likely caused by large growth and burn cycles. For a couple years the vegetation grows and expands and then during a year of severe weather, fires rage through large areas and burn a lot of that vegetation. Then depending on rainfall, the area then either grows quickly and replaces the fuel, or stays arid for a couple years before another large fire is sparked and has enough fuel to burn through.

![](./locations_by_year.gif)

   <img src="./plots/map_county_counts.png" alt="Example" width="800" height="">

## Modeling

In order to model and predict fire cause, I used only a handful of features. Specifically focused on date and location. Specifically Discovery Date, Owner Code, Reporting Agency, State, and Latitude and Longitude we used to predict the cause of fires. 

I explored using Logistic Regression, Decision Trees, Random Forests, KNN Classifier, and a Neural Network. Overall the KNN Classifier had the highest accuracy of around 92% on the validation set. 

At first I explored classifying all classes (excluding miscellaneous and missing data). This resulted in a fairly inaccurate model, with an accuracy of around 65%. Based on the confusion matrix listed below.
   

   <img src="./plots/Confusion matrix 1.png" alt="Example" width="800" height="">
   
Yet when looking at the spread of causes, some of the classes had such small counts, that it didn't make sense to model all categories as equal. For instance Debris burning was the most common cause of human caused fires, and they existed in every state. Therefore the model did not have enough information to pivot towards other fire causes. 

Therefore I attempted to model as two categories: human caused vs natural causes. When modeling with this binary class, I saw a significant increase in predictions. Yet our baseline started at around 20% of fires caused by lightning and 80% of fires caused by human causes. 

The KNN Classifying model (neighbors = 5) that I created ended up having an accuracy of 94% on train set, and a 92% on the validation set.
   
   <img src="./plots/Confusion Matrix 2.png" alt="Example" width="800" height="">


## Next Steps

I would like to possibly further explore these data and launch a dash board to better allow exploration. But I would like to further the connections between these data, MTBS (Monitoring Trends in Burn Severity) -- which provides LANDSAT pre and post images of over 20,000 of the US's largest fires, and NWS -- which provides polygons of fire watches/warnings/evacuations for each fire that threated populated areas.

### Weather

Weather plays a huge role in triggering and enticing a fire to grow in size. Being able to pull in weather data at the start and duration of a fire would assist with predicting the cause of the fire as well as the likelihood that that fire would spread quickly and expand. 


### Fire polygons

This dataset has a lot of information provided that would be useful to help examine the largest fires in the US. Specifically having the statistical cause of a fire and the reporting agencies involved along with the incident reporting ID, would assist with the ability to explore response times, fire warnings/watches/evacuation orders as provided by the NWS. 

## Conclusion

Overall I started this project trying to connect contextual data to predict fire severity and evaluate vulnerability by county. Due to difficulty connecting IDs across agencies, I pivoted the project towards predicting fire causes and further exploring these data that only recently became available. 

These data are still extraordinarily useful in the industry due to the ability to consider these data as fire ignition sources and fire occurrences in the US. Not all of these fires threaten society with danger. But studying the causes and spread of fires, from ignition to expansion would help reveal methods to better protect, better prepare, and better price fire risks. 





