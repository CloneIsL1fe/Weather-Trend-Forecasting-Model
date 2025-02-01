#Our Mission
 

By making industry-leading tools and education available to individuals from all backgrounds, we level the playing field for future PM leaders. This is the PM Accelerator motto, as we grant aspiring and experienced PMs what they need most – Access. We introduce you to industry leaders, surround you with the right PM ecosystem, and discover the new world of AI product management skills.

# Weather Trend Forecasting Model Documentation

## Introduction

This document provides a comprehensive overview of the Weather Trend Forecasting Model, detailing the data preprocessing, exploratory data analysis (EDA), model building, and evaluation techniques used to predict weather trends using machine learning approaches.

## Data Description

The dataset used for this model is extracted from Kaggle and contains various meteorological parameters, including:

- Country and location details

- Temperature (Celsius and Fahrenheit)

- Wind speed, direction, and pressure

- Precipitation levels

- Humidity and cloud cover

- Air quality indices (CO, Ozone, NO2, SO2, PM2.5, PM10)

- Sunrise, sunset, moonrise, and moonset times

## Data Preprocessing

Categorical Encoding:

- Columns that have objects are deemed categorical_columns and were label-encoded.

Handling Missing Values:

- Numeric columns were interpolated to fill missing values.

Outlier Removal:

- Applied Z-score filtering to remove extreme values.

Normalization:

- Min-Max Scaling was used for LSTM/GRU models. (The dataset is just 10k with 41 columns so kinda need to scale it down)

## Exploratory Data Analysis (EDA)

Trend Visualization:

- Temperature and precipitation trends were plotted over time.

Correlation Analysis:

- Used heatmap to visualize the relationships between weather variables.

Anomaly Detection:

- Isolation Forest algorithm was used to identify anomalies in temperature data.

## Model Building

### 1. LSTM Model

The dataset was transformed into sequences for time-series forecasting.

A Sequential LSTM model was built with:

- Two LSTM layers

- Dense layer for prediction

- Hyperparameter tuning using keras_tuner

Performance Metrics:

Mean Squared Error (MSE): 0.0204

Mean Absolute Error (MAE): 0.0988

Root Mean Squared Error (RMSE): 0.1429

Conclusion: Fairly accurate with the result being close to 0

### 2. GRU Model

Just the same as LSTM but GRU layers.

Performance Metrics:

MSE: 0.0189

MAE: 0.0988

RMSE: 0.1429

Conclusion: it did better with best guess is because GRU is simpler and with the data scaled made it more easier.

### 3. Ensemble Model

Combined LSTM and GRU predictions using averaging.

Performance Metrics:

MSE: 0.0170

MAE: 0.0909

RMSE: 0.1429

## Climate Analysis

Performed linear regression to analyze long-term temperature trends.

Plotted yearly temperature averages with trend lines.

## Environmental Impact Analysis

Examined correlations between air quality parameters and weather conditions:

- temperature_celsius
- humidity
- wind_mph
- air_quality_PM2.5
- air_quality_Nitrogen_dioxide
- air_quality_Carbon_Monoxide

Visualized using heatmaps.

Note: This can be added more parameters if needed.

## Feature Importance

Trained a Random Forest model to identify the most significant predictors of temperature.

Results were plotted as a feature importance chart.

## Spatial Analysis

Aggregated weather data by country.

Merged with geospatial data to visualize global temperature patterns.

## Conclusion

Overall, the model did great and have other added functions. On other note, the model could add an Input function where typing the country would result on the forecasting of its weather but it is not within my scope and would deem laborious.
