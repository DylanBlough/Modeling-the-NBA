## "This is How I Win:" Predicting the Outcomes of NBA Games

### Created by: Dylan Blough
[LinkedIn](https://www.linkedin.com/in/dylan-blough-b2185619a/) | [@BeerCanalytics](https://medium.com/@beercanalytics)

Using team stats from the first half of the NBA season, as well as historic stats, I will be building a model from scratch based on Dean Oliver's 4 Factors philosophy: https://squared2020.com/2017/09/05/introduction-to-olivers-four-factors/ in an attempt to model how close Oliver's weighting of the 4 factors comes to correctly predicting the outcomes of games, and if we we can re-weight them to generate better predictions.

As I progress and tweak my model I will be writing up my process on my Medium page, @BeerCanalytics, with what I learn! This project is geared towards those new to sports modeling and NBA analytics with the eventual goal of a full tutorial to create you're own betting model.

### Data Sources

Team statistics: BasketballReference.com (acessed using the SportsReference API)
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
