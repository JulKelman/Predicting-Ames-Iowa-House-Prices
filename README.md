# Predicting Ames, IA House Prices  
## Building the best predictive model for the portfolio feature of our App
---
#### Julia Kelman: [GitHub](https://github.com/JulKelman)  
  
  
## Problem Statement
---
We are a property management company providing services through an App for individuals who own multiple real estate properties. Our services include management, repairs, rent collection AND a portfolio feature that allows our clients to track the value of their properties.  
We are looking to expand to a new market and our sales team discovered that real estate, rental, and leasing is the number 4 industry contributing to the Iowa Gross Domestic Product ([source](https://www.iowadatacenter.org/quickfacts)). Since Ames, IA is the home of Iowa State University ([source](https://en.wikipedia.org/wiki/Ames,_Iowa)) and largely populated by students, we expect a large number of rental properties in this city which makes it the perfect place to roll out our App.  

We need to predict house prices with the highest level of accuracy for the portfolio feature of our App.  
We plan to solve this problem by using the Ames Housing Dataset to build a regression model able to predict house prices with the highest R^2 and lowest RMSE.   
This model will inform which features our employees should record data on during their monthly inspections. 

## Executive Summary 
---
Our goal is to build a model able to predict Ames, IA house prices with the highest predictive power for the portfolio feature of our App. In order to do so, the [Ames Housing Dataset](https://git.generalassemb.ly/julia-kelman/project_2/blob/master/datasets/train.csv) was used. This dataframe contains information provided by the Ames Iowa Assessor's Office and contains assessments of individual residential properties sold in Ames, IA from 2006 to 2010. To compile this dataset 2930 properties were assessed and 81 variables were provided for each of those homes. For a detailed list and description of those variables refer to the original [data dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt).  
A small portion of this dataset was reserved for a Kaggle competition and included in a [validation set](https://git.generalassemb.ly/julia-kelman/project_2/blob/master/datasets/test.csv). As a result our work was done on a subset of 2051 of those observations.  
The dataframe was cleaned, making sure to reformat any variables with data points wrongly assigned a null value. Non-numeric ordinal variables were reformated as well in order to be tranformed into numerical features. Dummy variables were created from the remaining non-numeric features in order to be included in our model. Finally, 2 new features were engineered.  
Exploratory analysis including summary statistics was performed to identify trends in the data. Data visualization tools were then used to visualize those trends and identify specific features that may be highly correlated to our target variable of sale price. Four models were tested: a baseline model, a linear regression model, a ridge model and a lasso model. The models were compared using R-squared and RMSE and the Lasso model was selected as the best preditive model. Further evaluation of the lasso model's performance and errors was performed.  
We concluded that a Lasso Regression model with most features included (75 variables: 73 of the 81 originals and 2 engineered) gives us the highest predictive power. We recommended that data be collected on all of those features during our montly home inspections. Additional specific recommendations concerning which feature to focus on during those assessments and the need for procedures during data collection were made. 


## Tale of Contents:
---
- [Ames Housing Data Import](#Loading-Data) 
- [Data Cleaning](#Data-Cleaning) 
- [Exploratory Data Analysis](#EDA) 
- [Model Preparation](#Model-Preparation)
- [Modeling](#Modeling)  
    - [Baseline Model](#Baseline-Model)  
    - [Linear Regression](#Linear-Regression)  
    - [Ridge](#Ridge)  
    - [Lasso](#Lasso)  
- [Model Selection](#Model-Selection)
    - [Predictions](#Calculating-Predictions)
    - [RMSE](#Calculating-RMSE)
    - [R-Squared](#Calculating-R^2)
    - [Model Comparaison](#Model-Comparaison)
- [Model Evaluation](#Model-Evaluation)
- [Conclusion & Recommendations](#Conclusion-and-Recommendations)
- [References](#References)
- [Kaggle Submission](#Kaggle-Submission)

## Project Files 
---
 [Ames Housing Training Dataset](https://git.generalassemb.ly/julia-kelman/project_2/blob/master/datasets/train.csv)   
[Validation Hold-Out Dataset](https://git.generalassemb.ly/julia-kelman/project_2/blob/master/datasets/test.csv)
[Cleaned Dataset](https://git.generalassemb.ly/julia-kelman/project_2/blob/master/datasets/cleaned_dataframe.csv)
## Data Dictionary 
---
[Data Dictionary Link](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)

## Main Findings
---
The 10 numerical features with the highest correlation with Sale Price are:
    1. Overall Quality
    2. External Quality
    3. Above ground living area Sq Ft(Gr Liv Area)
    4. Kitchen Quality
    5. Garage Area
    6. Garage Cars
    7. Total Basement Sq Ft
    8. 1st Floor Sq Ft
    9. Basement Quality
    10. True Total Rooms Above Ground (True TotRms AbvGrd)

The five features with the highest lasso model coefficients are:
    1. Above Ground Living Area
    2. Overall Quality
    3. Year Built
    4. Overall COndition
    5. Finished Basement 1 Sq Ft

## Conclusions and Recommendations 
--- 
A Lasso Regression model with most features included (75 variables: 73 of the 81 originals and 2 engineered) gives us the highest predictive power.

We recommend that data be collected on all of those features in order to have the highest predictive power. We recognize that collecting data on 75 variables may seem tedious. However, only 17 features are subject to change after initial assessment. We recommend to confirm with the operations team if they belive a lengthy initial assessment followed by shorter monthly assessments of those 17 features is reasonable.
In addition, we recommend to create a procedure for employees to collect data on those variables during the monthly assessments. Indeed, many of those features are qualitative in nature and all employees must assess them using the same approach in order for the values to be valid.
Finally, special attention should be given to the features with high correlation and high model coeficients identified above during those assessments. 

## References
--- 
[Iowa Quick Facts](https://www.iowadatacenter.org/quickfacts)  
[Ames, IA Wikipedia](https://en.wikipedia.org/wiki/Ames,_Iowa)  
[Data Dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)

