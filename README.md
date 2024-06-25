# Predictive Analysis of Bike Sharing Usage

## Table of Contents
1.	Introduction
2.	Problem Statement
3.	Business Goal
4.	Data Dictionary
5.	Loading and Inspecting the Data
6.	Exploratory Data Analysis (EDA)
7.	Data Preprocessing
8.	Feature Selection
9.	Modelling
10.	Evaluation
    
## Introduction
The objective of this analysis is to build a multiple linear regression model to predict the demand for bike rentals based on various features available in the dataset. The dataset contains daily records of bike rentals, along with weather conditions, seasons, and other relevant variables.
## Problem Statement
This assignment is a programming assignment wherein you have to build a multiple linear regression model for the prediction of demand for shared bikes. You will need to submit a Jupyter notebook for the same. 
## Business Goal
You are required to model the demand for shared bikes with the available independent variables. It will be used by the management to understand how exactly the demands vary with different features. They can accordingly manipulate the business strategy to meet the demand levels and meet the customer's expectations. Further, the model will be a good way for management to understand the demand dynamics of a new market. 
## Data Dictionary
- instant: record index
- dteday : date
- season : season (1:spring, 2:summer, 3:fall, 4:winter)
- yr : year (0: 2018, 1:2019)
- mnth : month ( 1 to 12)
- holiday : weather day is a holiday or not (extracted from http://dchr.dc.gov/page/holiday-schedule)
- weekday : day of the week
- workingday : if day is neither weekend nor holiday is 1, otherwise is 0.
+ weathersit : 
    - 1: Clear, Few clouds, Partly cloudy, Partly cloudy
    - 2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist
    - 3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds
    - 4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog
- temp : temperature in Celsius
- atemp: feeling temperature in Celsius
- hum: humidity
- windspeed: wind speed
- casual: count of casual users
- registered: count of registered users
- cnt: count of total rental bikes including both casual and registered
## Loading and Inspecting the Data
The dataset was loaded into a pandas DataFrame and basic inspections were performed to understand the structure of the data. This included checking for null values and generating summary statistics.
## Exploratory Data Analysis (EDA)
### Inspecting the Data
Initial inspections involved displaying the first few rows of the dataset and checking for null values to ensure data quality. Summary statistics were also generated to understand the distribution of the variables. Unique values for categorical values was also observed.
### Bivariate Analysis
Bivariate analysis was performed to explore relationships between pairs of variables:
•	**Numerical** vs. **Numerical**: Scatter plots and correlation coefficients were used.
•	**Categorical** vs. **Numerical**: Box plots were employed to visualize differences.
•	**Categorical** vs. **Categorical**: Cross-tabulation and stacked bar plots were used for exploration.
### Multivariate Analysis
A heatmap was used to show the correlation between numerical features, helping identify multicollinearity and potential interactions between variables.
## Data Preprocessing
### Dropping Unnecessary Columns
Columns that were not relevant to the predictive modeling, such as instant, dteday, casual, and registered, were dropped from the dataset.
### Mapping Categorical Variables
Categorical variables were mapped to more descriptive labels:
•	season was mapped to 'spring', 'summer', 'fall', 'winter'.
•	weathersit was mapped to 'clear', 'cloudy', 'lightrain', 'heavyrain'.
•	mnth was mapped to month names (e.g., 'Jan', 'Feb', etc.).
•	weekday was mapped to day names (e.g., 'Sun', 'Mon', etc.).
**One-Hot Encoding**
Categorical variables were one-hot encoded to convert them into a format suitable for modelling, ensuring no ordinal relationships were assumed among categories.
**Train-Test Split**
The dataset was split into training and testing sets to evaluate the model's performance on unseen data. The cnt column was used as the target variable, while all other columns served as features.
**Scaling**
Numerical columns (temp, hum, windspeed) were scaled using Min-Max scaling to normalize their range between 0 and 1.
## Feature Selection
### Recursive Feature Elimination (RFE)
Recursive Feature Elimination was used to select the most relevant features for the model. A linear regression estimator was employed, and the top 15 features were selected based on their importance.
Another Model was created , where 20 features were selected.
## Modelling
**Building the Model**
A multiple linear regression model was built using the selected features. The model was fitted on the training data, and the summary of the model was generated to evaluate the coefficients, significance levels, and overall fit.
## Evaluation
### Predicting and Evaluating on the Test Set
Predictions were made on the test set, and residuals were calculated to assess the difference between actual and predicted values. Various plots were generated to visualize the residuals and the relationship between actual and predicted values.
### Predicting and Evaluating on the Training Set
The same evaluation process was repeated for the training set to check for overfitting and ensure the model's predictions were consistent across both training and testing data.
**R-squared**: The final model achieved an R-squared value of approximately 0.846, indicating that the model explains 84.6% of the variance in bike rental counts.
**Adjusted R-squared**: The adjusted R-squared value of 0.842 confirms that the model generalizes well to new data.
**P-values**: Most features had significant p-values (<0.05), indicating they are statistically significant predictors of bike rental counts.
The analysis highlights the seasonal and weather-dependent nature of bike rentals, which can be crucial for optimizing bike-sharing operations.


**Author -Neeraj Singh**
