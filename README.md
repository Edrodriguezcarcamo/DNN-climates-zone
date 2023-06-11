Code developed for the paper: 
in revision

# Introduction

The aim of this code is to estimate the normal direct irradiance of solar radiation worldwide by using only one measured variable: the global irradiance. A deep neural network (DNN) is trained with minutely data from 49 meteorological stations of the Baseline Surface Radiation Network (BSRN). First, the stations are divided according to the Köppen and Geiger climate classification [1]. The world's climates are classified by Köppen into five major zones: tropical, dry, mild temperate, snow, and polar (A, B, C, D, and E, respectively). This classification use a three-letter nomenclature, with the first letter denoting the primary groupings and the subsequent letters denoting climatic subtypes, splitting the world into 31 subgroups. Then, the DNN is used in order to find the station that is considered as the "reference station". The reference station is the station used to train the DNN, where this pre-trained model was used to estimate the direct normal irradiance at the other stations belonging to its climate zone. Thus, 6 reference stations were found because the mild temperate zone was divided into the Cfa sub-zones and the rest of the stations for zone C. 

# How to use it

First, it is necessary to identify to which Koppen climate zone the station to be evaluated belongs. One way to identify which zone the station belongs to is to use the code made by Chen et al. [2] at http://hanschen.org/koppen. Each DNN trained with a reference station is saved as a Tensorflow .h5 file. The .h5 file names for the respective climate zones can be found in the table below. 

| Climate zone | Model name |
|-----:|-----------|
|A       |Tropical_NN_model.h5 |
|B       |Dry_NN_model.h5 |
|Cfa     |Cfa_NN_model.h5 |
|Rest of C  |C_rest_NN_model.h5 |
|D  |Snow_NN_model.h5 |
|E  |Polar_NN_model.h5 |

The input data to the model should be entered as a dataframe containing the following columns with a time step of 1 minute: 

| Column name | Variable |
|-----:|-----------|
|Clearness_index |Clearness index |
|Hourly_kT |Hourly clearness index |
|Daily_KT |Daily clearness index |
|N  |Daylight hours |
|Solar_altitud |Solar_altitud |
|AST |Apparent solar time |
|Persistence |Persistence coefficient |

The persistence coefficient is a value defined by Ridley et al. in [3]. 

# References

[1] Köppen, W., Geiger, R.. Handbuch der Klimatologie. 1930. doi:10.2307/200498.

[2] Chen, D. and H. W. Chen (2013): Using the Köppen classification to quantify climate variation and change: An example for 1901–2010. Environmental Development, 6, 69-79, doi:10.1016/j.envdev.2013.03.007.

[3] Ridley, B., Boland, J., Lauret, P.. Modelling of diffuse solar fraction with multiple predictors. Renewable Energy 2010;35(2):478–483. doi:10.1016/j.renene.2009.07.018.
