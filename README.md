![image](https://user-images.githubusercontent.com/65314799/100529621-07831100-31af-11eb-8223-eb39fe1a9817.png)


# Time Series Forecasting: Japanese Yen

For this project, I used time series forecasting and linear regression modeling to predict future movements in the value of the Japanese yen versus the U.S. dollar.

## Time-Series Forecasting

In the time_series_analysis notebook, I loaded historical Dollar-Yen exchange rate futures data and applied time series analysis and modeling to determine whether there is any predictable behavior.

![image](https://user-images.githubusercontent.com/65314799/100529640-300b0b00-31af-11eb-8f5d-db0ed9364b37.png)

Based on the plot of "settle" prices of yen futures, we can see a long-term strengthening of the Japanese Yen against the Dollar. There do seem to be some more medium, 1-3 year consistent trends, but on a daily basis, there are a lot of short-term ups and downs.

### Decomposition using a Hodrick-Prescott Filter 

![image](https://user-images.githubusercontent.com/65314799/100529645-4749f880-31af-11eb-8281-dfcb73ce3a1c.png)

Smoothing with the HP Filter and plotting the resulting trend against the actual futures returns, we can see that there's a lot of short term fluctuations that deviate around this trend. Perhaps these would represent profitable trading opportunities: For example, when the blue line deviates far below the orange, we can see this as a sign that the Yen is temporarily more undervalued than it should be (and, therefore, we'd see this as a short-term buying opportunity).

### Forecasting Returns using an ARMA Model

![image](https://user-images.githubusercontent.com/65314799/100529607-db679000-31ae-11eb-8ae1-be5888275f68.png)

I used an ARMA model to forecast returns and determined that the model is not a good fit based on all the p-values being greater than .05.

### Forecasting the Settle Price using an ARIMA Model

![image](https://user-images.githubusercontent.com/65314799/100529599-b6731d00-31ae-11eb-97b9-1ea8bd3d891e.png)

I used an ARIMA model to forecast returns and also determined that the model is not a good fit based on all the p-values being greater than .05.
The ARIMA model forecast shows that the Japanese Yen will increase at a linear rate in the next five days.

### Forecasting Volatility with GARCH

![image](https://user-images.githubusercontent.com/65314799/100529614-efab8d00-31ae-11eb-9ef6-cae95f7ba0f3.png)

The Garch model seemed to be good fit for predicting volatility because most of the p-values are below .05.

### Conclusions

* Based on my time series analysis, I would buy the yen when the settle price is below the trend line.
* The risk of the yen is expected to increase within the next five days.
* Based on the model evaluation, I do not feel confident in using these models for trading due to their p-values being higher than .05.

## Linear Regression Forecasting

In the regression_analysis notebook, I built a Scikit-Learn linear regression model to predict Yen futures ("settle") returns with lagged Yen futures returns and categorical calendar seasonal effects (e.g., day-of-week or week-of-year seasonal effects).

![image](https://user-images.githubusercontent.com/65314799/100529629-1b2e7780-31af-11eb-80e4-696e377734cb.png)

The model performs better with in-sample data (training data) because it has a RMSE of .415 as opposed to the RMSE of .565 of the out of sample data.

