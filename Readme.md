# MSBD5001 Kaggle Project Submission

https://www.kaggle.com/c/msbd5001-fall2020/overview

The dataset provides the average traffic speed per hour for a major road in Hong Kong from 2017 to 2018. There are missing speed data we need to fill in.

The data missing intervals are ranged from 1 hour to 9 hour:

```
Missing intervals 2018
0 days 01:00:00    3135
0 days 02:00:00    1260
0 days 03:00:00     526
0 days 04:00:00     217
0 days 05:00:00      75
0 days 06:00:00      30
0 days 07:00:00       8
0 days 10:00:00       2
0 days 08:00:00       2
0 days 09:00:00       1
```

## 1 Team

- Name: Chiu King Yuen
- Team name: nlgn
- Student Id: 20737245
- Email: kychiuau@connect.ust.hk or kingychiu@gmail.com

## 2 Environment

All works has been done on Kaggle notebook, here are the list of packages I used:

- numpy
- pandas
- sklearn
- tensorflow, keras
- lightgbm
- catboost

## 3 Reproducing the result

Snapshots of the notebooks and the submission files are also in this repository.

The submission 1, 2 notebook should be able to run on local machine directly with updated data file path.

If you cannot run the notebook, please let me know I can share the Kaggle notebooks directly.

### 3.1 Submission 1

Submission 1 is a all-in-one notebook export that contains all code to generate the submission file.

https://www.kaggle.com/kingychiu/cv-9-14-lb-9-82-submission-1?scriptVersionId=48558823

Result: Local MSE ~ 9.1181 Public Leader Board MSE ~ 9.82693

The first part of the notebook is the validation setup, I created some "date-holes" in 2017 data that simulate the missing-hour distribution in the 2018 data. This is to ensure we can use and validate the lag and moving windows features correctly.

After this, both the test set and validation set has similar distribution of nan in their prev-hour and post-hour. it is important because there can be 9 consecutive missing hours.

The modeling part is a weighted average of different models, the weighted average is performed with a LinearRegressor.

### 3.2 Submission 2

Submission 2 is a multi-stage training process and it is more risky. the 1 stage is similar to the submission 1, but the 2nd and 3rd stage use the N-1 stage prediction for filling missing speeds. The selected number of N is just 2 (2-stage), want to play safe.

It is potentially an overfitting result, the submission 1 is more robust. I have done a 10-stage one, the local MSE is 8.3983 but the Leaderboard mse became 10.xx

Result: Local MSE ~ 8.836 Public Lead Board MSE ~ 9.47404

- https://www.kaggle.com/kingychiu/multi-stage-submission-2/output?scriptVersionId=48562261
