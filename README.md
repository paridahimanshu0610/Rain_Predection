# Telco-customer-churn-prediction
## Context
Our objective is to forecast rain for the following day using classification models trained on the RainTomorrow target variable.

## Content
This dataset encompasses approximately a decade's of daily weather records gathered from various locations across Australia.

The focal point of our prediction is RainTomorrow, representing a binary outcome: Did it rain the subsequent day? The answer is either "Yes" or "No." Specifically, a "Yes" corresponds to days when rainfall measured 1mm or more.

The dataset utilized in this project has been sourced from [Kaggle's Rain In Australia](https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package). This dataset encompasses various categories of information, such as:

- Date: The date of observation

- Location: The common name of the location of the weather station

- MinTemp: The minimum temperature in degrees celsius

- MaxTemp: The maximum temperature in degrees celsius

- Rainfall: The amount of rainfall recorded for the day in mm

- Evaporation: The so-called Class A pan evaporation (mm) in the 24 hours to 9am

- Sunshine: The number of hours of bright sunshine in the day.

- WindGustDir: The direction of the strongest wind gust in the 24 hours to midnight

- WindGustSpeed: The speed (km/h) of the strongest wind gust in the 24 hours to midnight

- WindDir9am: Direction of the wind at 9am

- WindDir3pm: Direction of the wind at 3pm

- WindSpeed9am: Wind speed (km/hr) averaged over 10 minutes prior to 9am

- WindSpeed3pm: Wind speed (km/hr) averaged over 10 minutes prior to 3pm

- Humidity9am: Humidity (percent) at 9am

- Humidity3pm: Humidity (percent) at 3pm

- Pressure9am: Atmospheric pressure (hpa) reduced to mean sea level at 9am

- Pressure3pm: Atmospheric pressure (hpa) reduced to mean sea level at 3pm

- Cloud9am: Fraction of sky obscured by cloud at 9am. This is measured in "oktas", which are a unit of eigths. It records how many eigths of the sky are obscured by cloud. A 0 measure indicates completely clear sky whilst an 8 indicates that it is completely overcast.

- Cloud3pm: Fraction of sky obscured by cloud (in "oktas": eighths) at 3pm. See Cload9am for a description of the values

- Temp9am: Temperature (degrees C) at 9am

- Temp3pm: Temperature (degrees C) at 3pm

- RainToday: Boolean: 1 if precipitation (mm) in the 24 hours to 9am exceeds 1mm, otherwise 0

- RainTomorrow: The target variable. Did it rain tomorrow? References This total dataset is taken from following kaggle reference.

## Methodology

### Exploratory data analysis
1. Made count plots to show rain on the next day (target) with categorical inputs and histograms for numeric inputs.
2. Created a count plot to display rain on the next day based on different categories in the categorical input.
3. Used box plots to show how numeric features are distributed, separated by whether it rained the next day.
4. Showed correlation between numeric features using scatter plots.

### Data Preprocessing
1. Removed duplicate rows
2. Handled null values - Replaced null values in categorical features with most frequent categories and median/mode values in numerical features based on the distribution(i.e. skewed/normal).
3. Replace null values of RainToday feature using RandomForestClassifier.
4. Removed outlier data from numerical features.

### Data Manipulation
* Split data into training and test set with 10% of data being held out for testing.

### Feature Selection
1. Checking for correlation among features and removing correlated features.
2. Used Recursive Feature Elimination(RFECV) to select the numerical features.

### Feature Scaling
* Performed feature scaling using MinMaxScaler() 

### Predictive Modelling 
Applied the below models with hyperparameter tuning using GridSearchCV:
1. Logistic Regression
2. Support Vector Classifier
3. KNN
4. Decision Tree
5. Ensemble Methods-Random Forest, AdaBoost, Gradient Boosting, XGBoost
6. ANN
7. Naive Bayes

### Model Evaluation
Used the below metrics to compare the model's performance on test set:
1. Accuracy
2. F1 Score
3. ROC-AUC

### Model Selection
* Out of all the models we tested, the ANN model showed the best performance. It achieved an F1 score of 0.6, a test accuracy of 86.2%, and an AUC of 0.873.