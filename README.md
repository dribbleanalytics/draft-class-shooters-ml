# METHODOLOGY: Using machine learning to predict the top shooters in the 2018 draft

[Link to blog post.](https://dribbleanalytics.blogspot.com/2018/06/using-machine-learning-to-predict-top.html
)

## Data collection

First, I created a database of current NBA shooters. The restrictions for the database were as follows:

- All players were drafted in the 2013 draft or later. This restriction was set so that all the players who are used in the model have always been in the modern NBA, where teams shoot more threes.
- All players must have made at least 1 3PM/G in their NBA career. This is  because the NBA's minimum for league-wide 3PT% is 82 3PM, or 1 3PM/G.
- All players must have played at least half of the games they could have played since they were drafted. This is so the sample size for the players is large enough.
- All players must have played in college so that the comparison between competition is fair.

47 players met these restrictions. The following stats were recorded for each player's college and NBA career:

| College  | NBA |
| ------------- | ------------- |
| FG%  | FG%  |
| 2P%  | 2P%  |
| 3P%  | 3P%  |
| FT%  | FT%  |
| TS%  | TS%  |
| eFG%  | eFG%  |
| 3PAr  | PTS/G |
| FTr  | |
| PTS/G  | |

College data was taken from [Sports Reference](http://sports-reference.com/cbb), and NBA data was taken from [Basketball Reference](http://basketball-reference.com)

## Model creation

Using scikit-learn, I created three models: a linear regression, a ridge regression, and a support vector regression. Each model uses scikit-learn's train test split function with a test size of 20% (20% of the dataset is used to test the model's accuracy).

Each model's mean squared error and variance score (R^2) was measured to find the most accurate regression. The most accurate regression will have the lowest mean squared error and highest R^2.

## Predicting the top shooters in the draft

To predict the top shooters in the draft, I recorded the college data (all the same parameters as the college data for the original 47 players) of college players who met the following criteria:

- Are predicted to go in the first round of [The Ringer's 2018 NBA Draft Guide](http://nbadraft.theringer.com) as of the 5/21 update.
- Have 1 3PM/G in their college career.

I established no specific minimum for games played, as almost everyone played several games, except for Michael Porter Jr., who is excluded from this analysis.

The players' data was then put in to each of the three models to predict their points per game.
