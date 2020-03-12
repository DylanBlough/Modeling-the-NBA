## "This is How I Win:" Predicting the Outcomes of NBA Games

### Created by: Dylan Blough
[LinkedIn](https://www.linkedin.com/in/dylan-blough-b2185619a/) | [@BeerCanalytics](https://medium.com/@beercanalytics)

My first foray into basketball analytics was via Dean Oliver's 4 Factors philosophy: https://squared2020.com/2017/09/05/introduction-to-olivers-four-factors/. Ever since then, I have wondered how close just using those metrics would come to predicting the outcomes of games using Machine Learning to decide the importance (weightings of the factors.

My goal for this project is two-fold. First I want to test the accuracy of a model using Oliver's 4 Factors to see how accurate it is, and then try and build a model to surpass it in accuracy. Since we will be predicting the final scores of games, the metric for a model we will be looking at the most is Mean Absolute Error, or how many points away from the final score the model is. Analysis suggests that the Vegas point spreads in the NBA have Mean Absolute Error of around 8 so that will be my benchmark.

## Table of Contents

1. Data Sources
2. Data Dictionary
2. Repository Components
3. Conclusions

### Data Sources

Team statistics & box scores: BasketballReference.com (acessed using the SportsReference API)
Historic betting statistics: OddsSharks.com (to be included)

### Data Dictionary

| Column Name |                                   Definition                                   | Data Type |
|:-----------:|:------------------------------------------------------------------------------:|:---------:|
|     Team    |                                    Team Name                                   |   object  |
|      W      |                                      Wins                                      |   int64   |
|      L      |                                     Losses                                     |   int64   |
|      PW     |                                Pythagorean Wins                                |   int64   |
|      PL     |                               Pythagorean Losses                               |  float64  |
|     MOV     |                             Avg. margin of victory                             |  float64  |
|     SOS     |                              Strength of Schedule                              |  float64  |
|     ORtg    |               Offensive Rating: points scored per 100 posessions               |  float64  |
|     DRtg    |              Defensive Rating: points allowed per 100 possessions              |  float64  |
|     NRtg    |                       Net of Offensive & Defensive Rating                      |  float64  |
|     Pace    |                         Possessions per 48 minute game                         |  float64  |
|     FTr     |                    Free Throw Attempts / Field Goal Attempts                   |  float64  |
|     3PAr    |                         Field Goal Attempts from 3 pt.                         |  float64  |
|     TS%     | True Shooting %: measure of efficiency accounting for FT, 2pt FGs, and 3pt FGs |  float64  |
|     eFG%    |       Effective FG%: accounts that 3 pt FGs are worth more than 2 pt FGs       |  float64  |
|     TOV%    |                             Turnovers per 100 plays                            |  float64  |
|     ORB%    |                Percentage of possible offensive rebounds grabbed               |  float64  |
|    FT/FGA   |                            Free Throws / FG Attempts                           |  float64  |
|    OeFT%    |                    Opponent Effective Free Throw Percentage                    |  float64  |
|   TOV%  |       Turnovers per 100 plays      | float64 |
|   ORB%  |    Offensive Rebound Percentage    | float64 |
|  FT/FGA | Free throws per field goal attempt | float64 |
|  OeFG%  |   Opponent Effective Field Goals   | float64 |
|  OTOV%  |  Opponent Turnovers per 100 plays  | float64 |
|   DRB%  |    Defensive Rebound Percentage    | float64 |
| OFT/FGA |          Opponent FT / FGA         | float64 |

### Repository Components

1. This ReadMe providing an overview of the project, its goals and conclusions
2. A Code folder containing Jupyter Notebooks going through each step of the modeling process as well as separate notebooks for the different model experiments
3. A Datasets folder containing all of the stats and box scores scrapes. The box scores are broken out by year although the repo contains the combined and cleaned dataset as a separate file.

### Conclusions

I found that by using a Linear Regression model using only Oliver's factors performed with 66% accuracy and a MAE of 5. In other words, the model guessed the final scores 66% of the time with an average of 5 point error. I also ran a Grid Searched Random Forest model which scored 98% accurate with a MAE of .93. However, this model took around 7 hours to run, and incorporated 189 estimators. Future work on this project will be incorporating 10 game rolling averages of metrics for teams to start predicting future games, and incorporating Vegas odds information to indentify discrepencies that can be profited from.


