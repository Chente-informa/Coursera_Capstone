# Predicting the severity of car accident
                  September 27, 2020 
 
## 1. Introduction 

### 1.1 Background
To move for work, for see your family and friends, every day we use the road transports. But each use of the road is a risk of accident. Death or injury from traffic accident stay important each year and the effect of the ley begin to decrease strongly in France. Security of car is now better but if the death rate decreased, the accident with injury can be avoid too. Two measures continue to be strongly implemented, urban development for road safety, and awareness communication to citizens. Both need precision to have effect and have a big cost for the society.
We are all concerned, the State must guarantee our safety and everyone plays a role in increasing or decreasing the risk of accidents. 
### 1.2 Problem
Anyone can reduce the risk of an accident when we can predict the accident conditions that may occur, but we are not sufficiently educated. A particular accident zone is not sufficiently determined and the cause of the accident is sometimes unrecognized.
Data that might contribute to determine the cause of accident with severity of personal injury or death needs to be better identified and a forecasting system could detect a risk area and condition.
This project aims to predict severity risk and which condition (feature) will increase the risk.
### 1.3 Interest
The French road safety body needs a system to assess the risk of an accident based on geographic location and other criteria that most affect the risk of an accident. Insurance companies might be interested in using this model and features engineering to optimize thier coverage plans.

## 2. Data source and cleaning

### 2.1 Data sources
In France, data are shared in data.gouv.fr (FRANCE official open data).

https://www.data.gouv.fr/en/datasets/base-de-donnees-accidents-corporels-de-la-circulation/

Between 2016 and 2017, we are more than 120 000 accident cases.

##### Target prediction
There is characteristic information about accidents, locations, vehicles involved and victims.
Accident severity is provided on 4 levels, which are unbalanced. Except that for our objective of preventing any accident with bodily impact, we can group the values 3 and 4 in serious severity (death and serious injury) and 1 and 2 in slight severity (material or sligthly) and data are correctly balanced.

### 2.2 Preprocessing
Rows with too much missing data are dropped or if a column have too much nan value, it's not considerated like feature and dropped too.
Value of date of accident is split into day of the week (dayofweek column is created).
Likewise, the encoding of the hour of the accident is a little less obvious than that of categorical variables. 24 corresponding categories will be considered at each hour of the day. For example, 00:20 corresponds to category 0. The pm 4:32 time corresponds to category 16 (if this feature will not appears important, it will be possible to double the spliting at 48 half-hours or more) - I replaced the hrmn column.
15 regions are created with a K-means clustering of Latitude and Longitude in 18 regions - column geo was created.

### 2.3 Features engineering
To optimize the training of the model, firstly, the correlation and variance matrices are calculated.
The idea is that if variables are correlated, we can only keep one. This simplifies the data but can also make our model more robust since it reduces the impact of certain variables.
Regarding variance, it is an indicator of the dispersion of the values of a certain variable. If it is low for a given variable, it will mean that the impact of this variable is negligible. Removing it allows us to gain in efficiency.

features = ['mois', 'lum', 'int', 'atm', 'catr', 'circ', 'nbv','vosp', 'prof', 'plan', 'surf',
                'situ', 'catu', 'trajet', 'catv', 'dayofweek', 'geo'] in categories to encode in one-hot

and "an_nais" for age of person and "jour" for day of the month

### 2.4 Normalization
One-Hot encoding is chosen for categorical features with vectors composed of 0 everywhere and a 1 at the i -th modality using get_dummies from Pandas

### 2.5 Last balance adjustement
Checking the distribution of the target value of severity, we adjust the training set to stay balanced.


