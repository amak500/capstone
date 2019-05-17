## Executive Summary

This project provides an analysis and evaluation of the current and future indicators of movie revenue. Data was taken from an ongoing Kaggle competition. Methods of analysis include Linear Regression, Ridge Regression, Lasso Regression, Random Forest Regression, and XGBoost Regression. In particular, the method of analysis chosen to be productionalized was the XGBoost Regression model.  

The project also acknowledges that the analysis conducted has limitations: i.e, the dataset is relatively small and does not include enough information about foreign market films. 

## Problem Statement

I am looking to build a regression model to predict the amount of revenue a movie will make based on its metadata. My model performance will be judged based on RMSE, and I am hoping to improve upon my baseline score calculated by guessing the mean of every movie's revenue every time by at least 15 percent. 

My dataset is hosted by Kaggle, and can be found [here](https://www.kaggle.com/c/tmdb-box-office-prediction/). 

## EDA

The dataset originally contained 3000  movies. However, after cleaning the data and imputing and removing null values, I pared it down to 2775 values. Revenue distribution, along with runtime was skewed to the right. I chose not to use belongs_to_collection, imdb_id, id, original title, title, or overview as predicting features since I did not believe that they would be helpful for predicting movie revenue. I converted each movies' genres, production companies, production countries, cast, crew, and spoken languages into integer values, as there were too many to individually dummy out. I then extracted the top 20 actors and crew members of my dataset and dummied them out, so that each movie would have been checked for their participation. 

## Modeling

For my Naive model, I used the mean of my dataset as the prediction for every movie, and obtained a Root Mean Squared error of 158616484.34 dollars.  I used XGBoost, LinearRegression, Lasso, Ridge, and RandomForestRegressor models to try to predict movie revenue.  Out of the four, my XGBoost model performed the best, lowering the Root Mean Squared Error compared to the Naive model by 25 percent, to 121703294.48 dollars. Thus, I am choosing my XGBoost model to productionalize. Further hyperparameter tuning by adjusting learning rate, tree depth, and number of estimators yielded no noticeable decrease of RMSE. According to my model, the number of cast and crew members were the most important features in determining how much revenue a movie would yield.  

## Conclusions

Although my model did well when trying to predict revenues, overshooting the goal in my problem statement by 10 percent, my initial dataset was only 3000 reviews, which is a relatively small dataset. I would like to acquire more data specifically of non-English movies such as films from Bollywood or the Chinese film market. Additionally, given the time, in the future I would like to use principal component analysis to analyze movies' taglines and sypnoses to find out if there is any correlation between certain popular key phrases and movie revenue.