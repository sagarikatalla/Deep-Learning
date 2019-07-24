# Deep-Learning
Projects that use deep learning techniques in different use cases to make predictions 

#NTL1
•	Data: The dataset has 2500 observations and 17 columns where we use only percentiles of nighttime light (NTL) brightness as input variables for models to predict dependent variable, county-level population estimates.
•	Exploratory Data Analysis:
o	From the statistics for each variable, we can see percentiles of nighttime light (NTL) brightness per county have certain negative values maybe because of sensor error which was replaced with 0.
o	There were some counties with all NTL brightness variables as zeroes(like Dawson), possibly due to power outages caused by storms or other natural calamities in those counties. For example, in July 2015, a severe thunder storm flattened power lines in Dawson, Montana and during the same time, there was a hail storm in North Dakota. 
o	There are no missing values in the data.
o	From the histograms of the brightness quantiles, we can see that they all data distribution deviates from normal distribution, possesses positive skewness and high peakedness/ kurtosis.
o	From the correlation plot, we see that there is a positive correlation between population estimate and brightness values which increases as the quantile percentage of brightness increases and is most correlated to Q90, Q95. Also, multicollinearity exists as Q90, Q97pt5, Q95 and Q99 have strong correlation (>0.8).
•	 Modelling and Evaluation:
o	10-Fold cross validation was performed on the dataset by implementing three models: Linear regression, Random Forest, Gradient Boosting.
o	After parameter tuning, models with best accuracy for validation set were (in ascending order): Random Forest, Linear regression, Gradient Boosting.
o	While on training dataset, Random forest was the best model, both Regression and GBM performed equally.
o	Based on standard deviation of absolute and absolute percentage errors for training and validation sets, we can see that random forest is quite stable in its predictions compared to Linear regression and GBM, both of which have very high variability in errors.
•	Boxplots for CA:
o	There is an extreme outlier in the data, belonging to Los Angeles (LA) in California as all three models have given bad predictions. This could be because LA is the most populous county and is an extreme outlier with population close to 10 million.
o	All three models have right skewed distribution.
o	25% of data has zero absolute errors and all three models have almost same median.
o	Even though regression and random forest models have similar distribution till 75 % data, random forest has higher spread followed by regression and GBM respectively.
•	Boxplots for TX:
o	There are some extreme outliers in the data, belonging to Tarrant, Dallas which are highly populated in Texas as all three models have given bad predictions. 
o	All three models have very little variability in absolute and absolute percentage errors.
o	GBM has a very outlier error while other two models slightly better.
•	Boxplots for FL:
o	All three models have right skewed distribution.
o	Regression model has high variability in absolute errors, followed by random forest and GBM respectively.
o	Regression model has highest variability in absolute percentage errors and has large prediction errors for counties like Liberty leading to outliers, followed by GBM and random forest respectively.

#NTL2
•	Data: The dataset has 3142 observations and 484 columns where we use monthly VIIRS NTL data from 2013 to 2017, ALAND, AWATER as input variables for models to predict dependent variable, county-level population estimates.
•	Modelling and Evaluation:
o	10-Fold cross validation was performed on the dataset by implementing 2 models: Random Forest, Neural Network.
o	After parameter tuning, models with best accuracy for validation set were (in ascending order according to validation MAE): Random Forest, Neural Network.
o	While on training dataset based on MAE, Neural Network is a better model than random forest.
o	Based on standard deviation of absolute and absolute percentage errors for training and validation sets, we can see that random forest is quite stable in its predictions compared to neural network which has high variability in errors.
o	The model could have been better with
o	Lower number of epochs can improve the model
o	Increase or decrease in batch size can also help improve model performance
o	Higher number of nodes in hidden layer can improve accuracy of model
•	Boxplots for Absolute error:
o	California and Florida have right skewed distribution.
o	Texas has a symmetric distribution.
o	All three counties have almost same median.
o	California has highest spread amongst all with a high value outlier spreading the distribution, i.e. high error value.
•	Boxplots for Absolute percentage error:
o	Texas has the most right skewed distribution amongst the 3 counties.
o	Florida has a slightly right skewed distribution while California has a low spread symmetric distribution.
o	Texas has highest median, i.e. 50% population of errors have higher values than California and Florida.
•	Based on the training and test curves for each fold in cross validation, I feel 110 is the right number of epochs after which the model begins to overfit as observed in folds: 1,6,7.

