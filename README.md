# Predicting the severity of car accident
                  September 22, 2020 
 
## 1. Introduction 

### 1.1 Background
To move for work, for see your family and friends, every day we use the road transports. But each use of the road is a risk of accident. Death or injury from traffic accident stay important each year and the effect of the ley begin to decrease strongly in France. Security of car is now better but if the death rate decreased, the accident with injury can be avoid too. Two measures continue to be strongly implemented, urban development for road safety, and awareness communication to citizens. Both need precision to have effect and have a big cost for the society.
We are all concerned, the State must guarantee our safety and everyone plays a role in increasing or decreasing the risk of accidents. 
### 1.2 Problem
Anyone can reduce the risk of an accident when we can predict the accident conditions that may occur, but we are not sufficiently educated. A particular accident zone is not sufficiently determined and the cause of the accident is sometimes unrecognized.
Data that might contribute to determine the cause of accident with severity of personal injury or death needs to be better identified and a forecasting system could detect a risk area and condition.
This project aims to predict severity risk and which condition (feature) will increase the risk.
### 1.3 Interest
The French road safety body needs a system to assess the risk of an accident based on geographic location and other criteria that most affect the risk of an accident.

## 2. Data source and cleaning

### 2.1 Data sources
In France, data are shared in data.gouv.fr (FRANCE official open data).
Between 2016 and 2018, we are more than 200 000 accident cases.
##### Target prediction
There is characteristic information about accidents, locations, vehicles involved and victims.
Accident severity is provided on 4 levels, which are unbalanced. Except that for our objective of preventing any accident with bodily impact, we can group the values 2, 3 and 4 in serious severity (death and injury) and 1 in material severity and data are correctly balanced.
