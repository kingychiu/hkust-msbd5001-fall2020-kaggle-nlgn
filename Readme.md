# MSBD5001 Kaggle Project Submission

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

The submission 1 notebook should be able to run on local machine directly with updated data file path.

The submission 2 notebook is a multi-stage training on 3 kaggle notebooks. It might be hard to rerun.

If you cannot run the notebook, please let me know I can share the Kaggle notebooks directly.

### 3.1 Submission 1

Submission 1 is a all-in-one notebook export that contains all code to generate the submission file.

https://www.kaggle.com/kingychiu/cv-9-14-lb-9-82-submission-1?scriptVersionId=48558823

Result: Local MSE ~ 9.1181 Public Leader Board MSE ~ 9.82693

The first part of the notebook is the validation setup, I created some "date-holes" in 2017 data that simulate the missing-hour distribution in the 2018 data. This is to ensure we can use and validate the lag and moving windows features correctly.

After this, both the test set and validation set has similar distribution of nan in their prev-hour and post-hour. it is important because there can be 9 consecutive missing hours.

The modeling part is a weighted average of different models, the weighted average is performed with a LinearRegressor.

### 3.2 Submission 2

Submission 2 is a 3-stage training process and it is more risky. the 1 stage is similar to the submission 1, but the 2nd and 3rd stage use the N-1 stage prediction for filling missing speeds. It is potentially an overfitting result, the submission 1 is more robust.

Result: Local MSE ~ 9.8938 Public Lead Board MSE ~ 9.34230

- Stage 1: https://www.kaggle.com/kingychiu/1st-stage-random-state-2020
- Stage 2: https://www.kaggle.com/kingychiu/2nd-stage-random-state-2020
- Stage 3: https://www.kaggle.com/kingychiu/3nd-stage-random-state-2020
