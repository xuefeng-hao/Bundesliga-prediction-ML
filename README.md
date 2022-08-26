# Bundesliga-prediction-ML
## Pipline 
### Daten understanding
- Quelle: Historical Football Results and Betting Odds Data(https://www.football-data.co.uk/data.php)
- Row data from Bundesliga in session 2017-2021 ( Feature explanation see /data/Notes for football data)
- Basic backroud:
    - In Bundeslig matches in a year:
    - 306 matches 
    - 34 'Spieltag'(week)
    - 9 matches one week (full 18 teams in matching) 

### Feature engineering
- Initally select 5 basic features:
    - 'HomeTeam': home team name
    - 'AwayTeam': away team name
    - 'FTHG': Full Time Home Team Goals 
    - 'FTAG': Full Time Away Team Goals
    - 'FTR': Full Time Result (H=Home Win, D=Draw, A=Away Win)
- based on these features created intermediate features: 
    - HTGD: Home team goals difference (Calculate the cumulative goal difference per team per week)
    - ATGD: Away team goals difference
    - HTP: Home team cumulative points (Cumulative points for each team{ win: 3p; draw: 1p; lose: 0p})
    - ATP: Away team cumulative points
    - HM1,HM2,HM3 represents results of last 1/2/3 matches from home team(W:'win', D:'draw', L:'lose')
    - AM1,AM2,AM3 represents results of last 1/2/3 matches from away team
    - MW: in which week(Spieltag)
    - Get mean value divided by 'week', then override HTGD, ATGD ,HTP and ATP 
- freatures sorting:
    - drop the intermediate features, drop first 3 weeks data(not enough information)
    - drop'HTP','ATP'(which are highly correlated with HTGD, ATGD) 
    - dummy encodeing
- got final features: 'HTGD', 'ATGD', 'HM1_D', 'HM1_L', 'HM1_W', 'AM1_D', 'AM1_L', 'AM1_W', 'HM2_D', 'HM2_L', 'HM2_W', 'AM2_D', 'AM2_L', 'AM2_W', 'HM3_D', 'HM3_L', 'HM3_W', 'AM3_D', 'AM3_L', 'AM3_W'

### Model training and selecting
- Evaluate following models and compare the apperance 
    - Random Forests Model
    - XGBoosting Model
    - Support Vector Machines
    - Gradient Boosting Classifier
    - K-nearest neighbors
    - Gaussian Naive Bayes
    - Logistic Regression

- got the sore comparations:

### Model parameter tuning
- use grid-search for parameter selecting

