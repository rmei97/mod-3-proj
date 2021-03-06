### Prudential Risk Classification
This project based on a [Kaggle competition](https://www.kaggle.com/c/prudential-life-insurance-assessment/overview) by Prudential from 2016. 


#### Description
Life insurance has a problem. In this day and age buying life insurance is a hassle because of the many, many steps that take weeks to finish, which results in less people actually purchasing this. Prudential was looking for a way to make the process much more simplier; specifically by buildling a predictive model to classify the risk of new and existing customers. In this project, I create a data pipeline for cleaning data as it's feed into the model and a pipeline for using the data to make models. I produce a final XGBoost classifier to predict ordinal risk levels (1-8) with a final submission weighted kappa score of 0.56891 and an accuracy of 0.5754.



#### Data
Prudential provides a big csv file with almost ~60,000 rows and 128 columns. These columns are mostly of features relating to health such as age, height, weight, BMI, but there is also dummy variables to represent presence of a medical history and medical keywords. A big challenge is since this is health data, I don't have any idea of what the medical keywords or history are since they are formatted as vaguely (ex. Medical History 20, Medical Keyword 30). This would result in a limited final conclusion where I would only be able to point what the features. The target variable is risk level with oridinal values from 1 to 8.


![response variable graphs](/target_graph.png)


Exploring and cleaning the data set was a huge part of this project. I looked a lot of the different groups of variables (Medical Histories, Family Histories, Keywords). I predicted Medical Histories to be representing a length of characters of some sort since the distribution was so wide and led me to fill in the NA values with 0. Using some of my own prior knowledge of higher BMI more likely meaning unhealthier individuals, I compared the graph of that to the response variable. It didn't seem like there was an obvious pattern, but you could see a response value of 1 has a higher BMI on average than 8. Since it was not very straight I decided to graph the response to age. 


![response vs. bmi](/response_vs_bmi.png)


![response vs. age](/response_vs_age.png)


I saw the larger the age, the higher the risk. With this, I inferred the lower the risk level the higher the risk as a client. After looking at the correlation matrix for all my variables I was able to drop some variables from my model, and create some features such as summing up the number of medical keywords and average out family history values since there was a pattern of having partially filled values for any number of the columns. 


#### Modeling
For the modeling portion I attempted to use multiclass logistic regression (softmax), decision trees, random forest, and XGB. In the end, I was able to create a XGBoost classifier to obtain a weighted kappa score of 0.56891 and an accuracy of 0.5754. The weighted kappa score is a good metric to use because it penalizes the model for incorrect responses. I also tried to use feature importance to see which features seemed to be more important, but my pipeline for putting all the data together made the variables have even more indistinguishable names

![feature_importance](/feature_importance.png)


#### Conclusion
Again the end model that was best was the XGB. The feature extraction isn't as helpful as it should be; however, it does give an extra element to consider when trying to improve the pipeline. Though the model isn't the best model to have been come up with, I believe pairing it with the pipeline makes this project standout. Having the pipeline makes achieving the original goal of streamlining the process more real.


The next steps to make this project better would be to improve the pipeline to retain feature importance, and to standardize the cleaning process by thinking of the other possibilites inputs could be given in incorrectly. Another next step would to make the models better and training all the models within the pipeline for a longer time.


#### GitHub Contents:
home dir
  - <b>final.ipynb</b>: contains organized EDA and pipeline (cleaning, transforming, modeling)
  - <b>Life Insurance.pdf</b>: slides to presentation
  
notebooks dir
  - <b>EDA.ipynb</b>: main EDA notebook with code on data exploration and multiple graphs 
  - <b>continuous variables.ipynb</b>: notebook with eda on only continuous variables
  - <b>first.ipynb</b>: very first notebook containing preliminary EDA. Also contains code for writing transformations
  - <b>pipeline.ipynb</b>: main pipeline notebook containing pipeline itself and model evaluation
  - <b>pipeline-debug.ipynb</b>: notebook for trying different models and a go-to notebook for coding next-steps of this project
