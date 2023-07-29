# Sales Forecasting Read Me

## Overview
This project focuses on sales forecasting for Decathlon Singapore using the available sales data from 2020. The goal is to predict the turnover generated in the first three months of 2021, both for offline and online sales. To achieve this, several steps are followed, including feature preparation, data splitting, hyperparameter tuning, and model selection. Three different models are considered for forecasting: Elastic Net, XGBoost, and LSTM.

## Problem Statement
The task is to create a model that can accurately forecast both offline and online turnover for Decathlon Singapore from January 2021 to March 2021. The provided dataset contains sales data from 2020, which will be used for training and validation, while the data from 2021 will be used as test data.

## Feature Preparation (Section 2.c)
In this section, a function called `get_rolling_average()` is defined. This function calculates the ratios of 2, 5, and 7-day rolling averages of the aggregated turnover values. The data is split into training and validation sets, with 80% for training and 20% for validation.

## Preparing Train, Validation, and Test Data (Section 2.d)
The training and validation data is split into X and y, with X containing the features and y containing the target variable (total turnover). The shapes of each data object are printed.

## Prepare Hyperparameter Tuning Data (Section 2.e)
In this section, three types of data objects are prepared for hyperparameter tuning:
1. X data objects with only date features.
2. Scaled data for the aggregation features (date features should not be scaled).
3. XGBoost feature selection data, which includes different numbers of top features (5, 10, 15, and all 19).

## Model Building (Section 2.g)
This section focuses on building three different models:
1. Elastic Net Model: It uses two hyperparameters, alpha and l1 ratio, for regularization.
2. XGBoost Model: It uses max depth and subsample as hyperparameters for tuning.
3. LSTM Model: It uses the dropout rate as a hyperparameter.

## Aggregation and Date Features vs Only Date Features (Section 2.h)
The Elastic Net Model is used to compare the performance of using both aggregation and date features versus using only date features. The evaluation is based on RMSE and the ability to capture seasonality trends.

## Model Selection (Section 2.i)
The best model is selected from the three models built earlier. The Elastic Net, XGBoost, and LSTM models are evaluated based on their RMSE and ability to capture seasonality trends. Model selection and hyperparameter tuning followed a greedy approach, where each model/parameter combination was tried once. If the root mean squared error (RMSE) was higher, not all permutations were tested. Nevertheless, it is practically unlikely that a better model exists.

## Hyperparameter Tuning (Section 2.j)
In this section, hyperparameter tuning is performed specifically for the XGBoost model. Different combinations of scaling, model parameters (max depth and subsample), and feature selection (top 5, 10, 15, and all 19 features) are tested and compared based on RMSE.

## Conclusion
The sales forecasting project utilized a greedy approach for model selection and hyperparameter tuning, where each model/parameter combination was tested once. If the root mean squared error (RMSE) was higher, not all permutations were explored. However, based on the results obtained, it is unlikely that a significantly better model exists.

The forecasting process relied on aggregated data based on the mean of the same month of the quarter and day. While this approach might not perfectly align with the strong day-of-week effect, it still resulted in a relatively low RMSE and effectively captured seasonality patterns.

It is worth noting that the data available for training only included Q3 and Q4, and the holiday season sales increase in December had an impact on the forecasted data for March. This may introduce some bias into the forecasts, and further analysis is recommended to understand its potential implications.

### Business Insights and Recommendations

1. **Potential for Online Sales Growth**: The time series forecast results indicate that online sales remain relatively low compared to offline sales. This presents a significant opportunity for Decathlon to focus on growing the online market and capturing a larger customer base. An omnichannel approach, where customers can seamlessly switch between online and offline shopping, can create a cohesive and consistent brand experience, driving customer loyalty and engagement. Enhancing the online shopping experience through user-friendly interfaces, streamlined checkout processes, and personalized recommendations can significantly boost online sales and customer retention.

2. **Stable and Predictable Market Environment**: The consistent trends observed in the forecasted data indicate a stable and predictable market environment. This stability provides valuable insights for the business to make informed decisions and capitalize on existing opportunities. Decathlon can focus on targeted marketing strategies that have proven to be effective in the past, leading to better utilization of marketing budgets and a higher return on investment. Additionally, stable trends enable the optimization of the supply chain and inventory management. Accurate demand forecasting can help avoid stockouts and overstock situations, leading to cost savings and improved customer satisfaction.

The sales forecasting model, based on XGBoost with tuned hyperparameters, provides a reliable tool for Decathlon Singapore to plan for the first three months of 2021. By leveraging the insights gained from this analysis, the company can make data-driven decisions to achieve its business objectives and maximize its sales and profitability. As with any forecasting model, continuous monitoring and validation against actual sales data are crucial to ensure the model's ongoing accuracy and relevance.
