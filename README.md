# Machine Learning Engineer Nanodegree
## Capstone Proposal
Marcel Makoto Kondo
October 5th, 2019

## Proposal

### Domain Background
  As one of the fastest growing industries in present years, the gaming scenario has seen a surge of interest almost never seen before, with worldwide competitions taking place in gigantic stadiums, crouds comparable to those of football matches, and viewers in massive quantities not only physically but also virtually through webstreams throughout the whole world. With audiences as massives as those, the ability to provide in-game statistics, and further commentaries on what they represent for the performance of the team or player, is an important aspect to develop. However, with games getting more and more complicated, with mechanics that involve increasingly more detailed information, this task has become quite difficult to be done by human commentators all by themselves - and therein lies a possible application for machine learning methods to aid them.

### Problem Statement
  The problem which this project is aimed at tackling is the Kaggle competition "PUBG Finish Placement Prediction", in which we have to try and predict the final placement of numerous players in one round of the famous FPS title "Player Unknown's Battle Ground", by analising data 
realated to their score throughout one round (such as kill count, assists, damage dealt, etc). 

  As we have at our disposal a collection of over 65000 games' worth of anonymized player data, consisting of their score data + their final placement, this problem is a well suited application for supervized learning algorithms, and I plan to test and compare the performance of 3 different algorithms (described in the Solution Statement) in that category.
  
  The link to the kaggle competition can be found bellow:
  https://www.kaggle.com/c/pubg-finish-placement-prediction/overview

### Datasets and Inputs
  Since the problem in question consists of a Kaggle competition, the training dataset was already provided. It consists of a table with 29 columns, of which 2 are the player's ID and his respective normalized final placement(0.0 meaning last place and 1 first place), and the others consist mostly of numerical values describing their statistics (from now on reffered to as features) at the end of the game.

### Solution Statement
  As mentioned earlier, the problem at hand is well suited for supervized learning algorithms. Moreover, as the target varibale (the normalized final placement) can have any real value in the range [0,1], we have to utilize regression algorithms.
  
  My plan is to test and compare 3 different aproaches to regression: LASSO regression, Ridge regression, and LASSO regression with dimensionality reduction using Linear Discriminant Analysis.
  
  The reasoning behind those choices were mainly to evaluate the performance of two well known types of regressors at the problem at hand, plus a comparison to see how much a pre processing step on the data, such as dimensionality reduction, affects the performance of a regression.
  
### Benchmark Model
The benchmark model to be used for comparison in this project is planned as a simple linear regression based on least squares with no preprocessing of data, and shall be measurable through the same metrics as described in the Evaluation Metrics session.

### Evaluation Metrics
The metric to be used to evaluate the performance of the algorithms is the one defined by the competition rules: Mean Absolute Error (MAE).

MAE score is defined as the mean of the absolute value of the real minus predicted values of each row in the validation/test data sets: 1/n sum(abs(each_predicted_y-each_real_y))) The advantage of MAE (other than being a contest requirment) is that it provides a simple measurement of the error of a prediction that disregards the sign of the error and doesn't over-emphasize outliers.

### Project Design
The project's workflow can be divided into 6 different steps:
 * Data analysis 
 * Pre-processing
 * Benchmark model 
 * Algorithm training
 * Comparison of algorithms 
 * Final algorithm selection 
 
#### Data Analysis
Since each player described in the database has 27 different features, and they each represent to a different in-game statistic for one round, this step is thought out to explore the details and possible particularities of some of those features, and potentially find through simple inspection a subset of those features that intuitively correlates to the target variable.

#### Pre-processing
This step encompasses every data manipulation process that will be needed in the following steps, such as gap corrections and train and test splits. In this step a separate dataframe corresponding to the the dimensionally-reduced data shall also be created and put aside for use in a following step.  

#### Benchmark Model
This step consists of running a simple linear regression model on the data in order to establish a baseline performance for future comparison.

#### Algorithm training
This step consists of the training of the models on the training dataset and their preparation for evaluation according to the evaluation metric.

#### Comparison of algorithms
The comparison of each algorithm's performance will be done according to the previously established metric, with regards to the "local" test database (originated from the train/test split done in the pre processing step). 

#### Final algorithm selection
The algorithm with the best "local" performance will be the one chosen to be submitted to the competition in order to extract a score and an overall position with regards to entries submitted by other users.
