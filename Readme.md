## market_value_perdiction

### Overview

For this project, I scraped performance data of football players from [Transfermarkt.de](transfermarkt.de) merged it with [Kaggle's FIFA '18]() data set with the goal of building a **predictive model for players' market value based on physical attributes, performance data, and skills.** Currently, the best performing model uses sklearns `GradientBoostingRegressor()` and achieve a **validation accurary of ~80%**

The next, step in this project will be to **identify overvalued/undervalued** players by excluding some players in the training phase of the model and comparing their predicted market value to their market value listed on transfermarkt.de or the transfer fees paid for the individual players. 

** Note: This repository is still somewhat a work in progress.

### The Data

#### Transfermarkt.de

The ![datset scraped from transfermarkt.de](data/tm.csv) contains features of approx. 5000 football players from 15 European top leagues. In the raw data, some of the feature names are in German and others are non-descriptive (I'll change that soon) - below I have listed them based on how I intend to change them: in English & with descriptive names.  


**The first 8 variables contain general information** on the player:

|'player_name'|'birth_month'|'days_on_team'|'days_contr_end'|'days_since_contr'|'Alter.'|'Größe.'|'Social.Media.|
|---|


**The other variables contain the following performance data** for every league contained in the data:

|'games_played'||
|---|


### Kaggle FIFA '18

A detailed description of Kaggle's FIFA '18 dataset can be found here: [Kaggle FIFA '18]()

In this repository the data is saved here: [Kaggle FIFA '18 in Repo](data/fifa.csv)




### Results
