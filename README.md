# README 
## Project 2: Ames, Iowa Housing Data
### Contents:
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Data Import and Cleaning](#Data-Import-and-Cleaning)
- [Preliminary EDA](#Preliminary-EDA)
- [Feature Engineering](#Feature-Engineering)
- [Model Interpretation](#Model-Interpretation)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)

### Problem Statement
In this project we were tasked to take a dataset of housing sales in Ames, IA and transform them into actionable recommendations for real estate investors. The data was collected from 2006 to 2010 and contained 2930 observations, with a total list of 82 variables. Given this information, the goal is to create a model that will accurately predict the sale price of homes, based on the features and data contained in the observations to help real estate investors, real estate professionals as well as current and prospective homeowners accurately judge their portfolios and prospective investments.

### Executive Summary 

The process of analyzing the Ames Housing Data  begins by importing and cleaning a training data set of 2051 homes with 82 different features. This process involved removing unnecessary features and changing data types to be able to visually examine the relationships between the features and the target variable, SalesPrice. After the data is in a more analysis-friendly format, we are able to identify some features that exhibit strong linear relationship with SalesPrice, as these will be the starting points for our predictive model. The highest correlation with SalesPrice for all features is OverallQual, or Overall Quality. This feature is an ordinal, numeric value that ranges from a low score of 1 (Very Poor) to 10 (Very Excellent). This makes sense as it represents the rating of the overall material and finish of the house, arguably containing most of the features and data that we will be diving into. 

### Data Import and Cleaning
Due to the necessity of converting categorical variables to numerical values, I applied a rating map to all ordinal categorical features and then applied one-hot encoding on nominal variables to create dummy variables. The model is then fit using OLS, Ridge and Lasso regressions, at which point we calculate the following metrics: $R^2$ and Mean Cross Validation Score.

### Model Interpretation
Lasso Model Scores:
 - RMSE Score for Training Data: 22430.68503843556
 - RMSE Score for Test Data: 22226.41357888047
 - R^2 Score for Train Data: 0.9210862530033597
 - R^2 Score for Test Data: 0.9176982805183043

Although our models were fairly close in their results, the differences between the train and test splits paint a clear picture as to which model was superior. Given the baseline scores for Linear Model Scaled, Lasso and Ridge, it is apparent that our Lasso model has done the best. This is demonstrated by the difference between the RMSE as well as R^2 scores for train and test data, exhibiting the lowest bias and lowest variance. Additionally, the fact that the training RMSE is higher than the testing RMSE demonstrates that the model is in fact underfit, meaning that it should be able to generalize well to unseen datasets. Further, we can say that the score of 0.9176982805183043 means that our model can account for 91.76982805183043% of the variance of y, or SalePrice, compared to a model with no predictors.

Additionally, our model is limited in the time period of the data collected, which may be impacted by the global financial crisis of 2007-08, as the real estate market was directly impacted by the repercussions of the market dynamics.

### Conclusions and Recommendations
After obtaining, cleaning, visualizing and modeling the data, it is now apparent for our audience as to the major drivers of real estate pricing for SalePrice of homes. Although this is taken from data in Ames, IA, the fact that our model is underfit lends credence to its ability to generalize well to other data. 

In looking at the coefficients that have the highest magnitude, we can provide some recommendations for better understanding the potential values of your real estate or to predict the price of a house. First, the Exterior Quality and Masonry Veneer Area are both areas in which there is a strong positive coefficient, meaning that efforts to improve them should positively impact the Sale Price. On the other hand, the negative coefficients of  both veneer styles of brick (face and common) and the Roof Style of "Mansard" should steer any investor or owner away from investing. 

Next steps that I recommend to take include obtaining additional data sets to feed into our models, so as to better understand the model's generalizability. Additionally, there are other regularization tools that could be employed, such as the ElasticNet regression, as well as also statistical methods that were not approached in this model. Including polynomial features by multiplying the predictive power of each of our 197 rows would also potentially yield more insights as to how the price of homes can be predicted.

