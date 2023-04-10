# Kaggle Titanic Machine Learning Project

Author: Jean-Charl Pretorius

### Files

The jupyter notebook [titanic-solution.ipynb](titanic-solution.ipynb) contains all of the code for the project.

The training and testing data sets are [train.csv](train.csv) and [test.csv](test.csv), respectively.

## Topic being investigated

For my final project in ENSF 611 I am going to investigate the Titanic dataset from Kaggle and submit my results to participate in the training competition.

### Dataset

[Titanic Disaster Competition](https://www.kaggle.com/c/titanic)

[Data](https://www.kaggle.com/competitions/titanic/data)

### Steps

1. Load and Visualize the data
2. Preprocessing data: feature engineering and handle missing data
3. Split data into training and testing sets
4. Compare models with cross validation
5. Hyper parameter tuning with GridSearchCV
6. Re-train model on best parameters
7. Make predictions and submit results

### Models Investigated

- `BernoulliNB()`
- `LogisticRegression(max_iter=2000, random_state=55)`
- `SVC()`
- `RandomForestClassifier(random_state=55)`
- `GradientBoostingClassifier(random_state=55)`

## Results

The best model I trained was a Gradient Boosting Classifier with an accuracy score of 0.87

The predictions I submitted achieved an accuracy of 0.78229 on Kaggle. At the time of this first submission, this was enough to place #2605 on the Kaggle leaderboard.

There were significantly more false negatives (94 passengers predicted to have perished but actually survived) than false positives (23 passengers predicted to have survived but actually perished), which resulted in a higher precision (0.91) than recall (0.72).

The gradient boosting classifier outperformed all of the other models tested. After re-training the model on the entire training data set we achieved an accuracy of 0.87, which is quite a bit higher than the Kaggle score. This suggests that the model is overfitting the data. When we consider a relatively simple dataset like the Titanic disaster it is easy to overfit the data. In the context of this dataset, overfitting is not of much concern since there will never be any new data to apply this model to, because there is obviously not going to be any more RMS Titanic sinking in the future.

## Reflection

I selected this problem to solve because I wanted to try doing a Kaggle competition and see how I can apply the models, preprocessing, and tuning techniques I learned the the course on my own. I was interested in getting a deeper understanding of such a notable historic disaster and the Titanic dataset was recommended as a good competition to start with for new Kaggle users.

There were no major deviations in my process of analyzing the data and applying the models from what I had planned in my project proposal. The Lab 3 assignment was a good template to base this project off of. I include the techiques of using a column transformer and a pipeline to my cross-validation and grid search sections so that I was properly handling the separation of which data was being used to fit the scalar and encoder. I did add the inclusion of BernoulliNB in the cross-validation section, and I unfortunately did not have time to extend the models investigated to include XGBoost.

The most difficult part of this project was the feature engineering and preprocessing step. I spent a lot of time figuring out what to do with the different categorical and non-categorical data, and I could have even spent much more time on it to improve my results. I learned a lot about proper preprocessing of data and how to separately scale or encode different columns in the same table. I gained a better understanding of how naively fitting a scaler on the data can 'leak' information from the test set into the parameter and model selection. Visualizing the data at the beginning was very useful and gave a good insite to which features could be important for the models.

If I had more time I would have liked to see how the passenger's titles in their names could be used as features. Maybe a higher class title could be a predictor of survival, or I could have used the titles such as 'Master' or 'Miss' to signify that the passenger is younger when imputing missing age values.

I could have done something with the cabin names as well, such as grouping them by their section letter. I ultimately decided to drop that feature because of the large number of null values, but it may have been meaningful to keep the null values as their own class.

Seeing how my submission ranked on Kaggle was motivating to try out other competitions in the future.
