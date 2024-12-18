# SARIMA_model

The purpose of this notebook is to apply time series analysis techniques to forecast sales data, using both econometric models (e.g., SARIMA) and machine learning (e.g., Random Forest). The dataset is monthly champagne sales from 1964 to 1972.

**1. Data Loading and Preprocessing** The dataset was loaded, reindexed and split into training (1964-1969) and testing (1970+) sets for out-of-time evaluation.

**2. Exploratory Data Analysis** The time series shows trends, seasonality, and non-stationarity. Additive and multiplicative seasonal decomposition models were used to isolate and visualise trends, seasonality and residual noise. A SARIMA model was picked to analyse the data, straight from the original time series. 

**3. Stationarity and Differencing** Strong seasonality was confirmed using the Augmented Dickey-Fuller test and the autocorrelation function (ACF). Seasonal differencing with a 12-month lag (D=1, m=12, d=0) sufficiently stationarised the series.

**4. SARIMA Modeling** SARIMA parameters p and q were proposed, then optimised using pmdarima auto_arima. The best model was SARIMA(0,0,0)(0,1,0)[12]. 

**5. Machine Learning Approach** A Random Forest model was trained on lagged sales features (x_1 to x_12). The Mean Absolute Percentage Error (MAPE) for 1-month horizon predictions was 0.16. Feature engineering was explored to reduce the MAPE to 0.15, using additional rolling and exponential moving average features. 

**6. Out-of-Sample Forecasting** A Random Forest model was trained for each prediction horizon. The model's MAPE was then compared with SARIMA's. Machine learning models improved out-of-sample forecasts compared to SARIMA's static seasonal predictions.
