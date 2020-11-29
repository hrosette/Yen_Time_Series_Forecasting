# Time Series Forecasting: Japanese Yen

For this project, I used time series forecasting and linear regression modeling to predict future movements in the value of the Japanese yen versus the U.S. dollar.

## Time-Series Forecasting

In the time_series_analysis notebook, I loaded historical Dollar-Yen exchange rate futures data and applied time series analysis and modeling to determine whether there is any predictable behavior.

### Decomposition using a Hodrick-Prescott Filter 


Smoothing with the HP Filter and plotting the resulting trend against the actual futures returns, we can see that there's a lot of short term fluctuations that deviate around this trend. Perhaps these would represent profitable trading opportunities: For example, when the blue line deviates far below the orange, we can see this as a sign that the Yen is temporarily more undervalued than it should be (and, therefore, we'd see this as a short-term buying opportunity).

### Forecasting Returns using an ARMA Model


I used an ARMA model to forecast returns and determined that the model is not a good fit based on all the p-values being greater than .05.

### Forecasting the Settle Price using an ARIMA Model

I used an ARIMA model to forecast returns and also determined that the model is not a good fit based on all the p-values being greater than .05.
The ARIMA model forecast shows that the Japanese Yen will increase at a linear rate in the next five days.

### Forecasting Volatility with GARCH

The Garch model seemed to be good fit for predicting volatility because most of the p-values are below .05.

## Conclusions

* Based on my time series analysis, I would buy the yen when the settle price is below the trend line.
* The risk of the yen is expected to increase within the next five days.
* Based on the model evaluation, I do not feel confident in using these models for trading due to their p-values being higher than .05.

## Linear Regression Forecasting

In the regression_analysis notebook, I built a Scikit-Learn linear regression model to predict Yen futures ("settle") returns with lagged Yen futures returns and categorical calendar seasonal effects (e.g., day-of-week or week-of-year seasonal effects).



The model performs better with in-sample data (training data) because it has a RMSE of .415 as opposed to the RMSE of .565 of the out of sample data.

