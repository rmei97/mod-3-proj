# mod-3-proj
This project based on a kaggle competition by Prudential from 2016. (https://www.kaggle.com/c/prudential-life-insurance-assessment/overview)

# Description
In this project I made a pipeline from the given dataset to produce a predictive model for classifying ordinal risk levels (1-8). Using XGBoost got me a final submission weighted kappa score of 0.56891 when the highest is around 0.67. Given more time, I would want to run more models and apply a gridsearch to tune my hyperparameters.


# Contents:
home dir
  - <b>final.ipynb</b>: contains organized EDA and pipeline (cleaning, transforming, modeling)
  - <b>Life Insurance.pdf</b>: slides to presentation
  
notebooks dir
  - <b>EDA.ipynb</b>: main EDA notebook with code on data exploration and multiple graphs 
  - <b>continuous variables.ipynb</b>: notebook with eda on only continuous variables
  - <b>first.ipynb</b>: very first notebook containing preliminary EDA. Also contains code for writing transformations
  - <b>pipeline.ipynb</b>: main pipeline notebook containing pipeline itself and model evaluation
  - <b>pipeline-debug.ipynb</b>: notebook for trying different models and a go-to notebook for coding next-steps of this project
