## market_value_prediction

### Overview

For this project, I scraped performance data of football players from [Transfermarkt.de](transfermarkt.de) and merged it with [Kaggle's FIFA '18](https://www.kaggle.com/kevinmh/fifa-18-more-complete-player-dataset) data set to build a **predictive model for players' market value based on physical attributes, performance data, and skills.** 

**Currently, the best performing model uses sklearns `GradientBoostingRegressor()` and achieve a validation accurary of ~80%**

The next, step in this project will be to **identify overvalued/undervalued** players by excluding some players in the training phase of the model and comparing their predicted market value to their market value listed on transfermarkt.de.

**Note**: This repository is still somewhat a work in progress.

### The Data

#### Transfermarkt.de

The [data set scraped from transfermarkt.de](data/tm.csv) contains features of approx. 5000 football players from 15 European top leagues. In the raw data, some of the feature names are in German and others are non-descriptive (I'll change that soon) - below I have listed how I intend to change them: in English & with descriptive names.  


**The first 8 variables contain general information** on the player:

* 'birth_month'
* 'days_on_team'
* 'days_contr_end'
* 'days_since_contr'
* 'age'
* 'height'
* 'position'
* 'social_media'


**The other variables contain the following performance data** for each league:

1. For outfield players:

* 'games_played_[LEAGUE]'
* 'goals_scored_[LEAGUE]'
* 'assists_[LEAGUE]'
* 'num_yellow_cards_[LEAGUE]'
* 'num_second_yellow_[LEAGUE]'
* 'num_red_card_[LEAGUE]'
* 'minutes_played_[LEAGUE]'

2. For goalkeepers: 

* 'games_played_[LEAGUE]'
* 'goals_scored_[LEAGUE]'
* 'num_yellow_cards_[LEAGUE]'
* 'num_second_yellow_[LEAGUE]'
* 'num_red_card_[LEAGUE]'
* 'goals_against_[LEAGUE]'
* 'shutouts_[LEAGUE]'
* 'minutes_played_[LEAGUE]'



### Kaggle FIFA '18

A detailed description of the FIFA '18 data set from Kaggle can be found here: [Kaggle FIFA '18](https://www.kaggle.com/kevinmh/fifa-18-more-complete-player-dataset)

In this repository the data is saved here: [Kaggle FIFA '18 in Repo](data/fifa.csv)


**Note:** In the data wrangling process some of the above variables were excluded for different reasons. For example, the 'highest_mv' variable from the transfermarkt.de data was excluded because it is too predictive of the target variable 'market_value'.


## The Scripts

### merge.Rmd

[merge.Rmd](src/merge.Rmd) takes the two data sets ([Kaggle FIFA '18](data/fifa.csv), [Transfermarkt.de](data/tm.csv)) and merges them on 'name' and 'birth_date' assuming that these two variables together constitute a unique identifier.


### mv_prediction.ipynb

[mv_prediction.ipynb](src/mv_prediction.ipynb) uses the merged data set created by [merge.Rmd](src/merge.Rmd) does some cleaning and feature engineering and finally test different machine learning models to predict the players market value.
