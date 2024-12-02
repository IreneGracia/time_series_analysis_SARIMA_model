# SARIMA_model

The purpose of this notebook is to apply time series analysis techniques to forecast sales data, using both econometric models (e.g., SARIMA) and machine learning (e.g., Random Forest). The dataset is monthly champagne sales from 1964 to 1972.

**1. Data Loading and Preprocessing** The dataset was loaded, converted to a time-series index, and split into training (1964-1969) and testing (1970+) sets for out-of-time evaluation.

**2. Exploratory Data Analysis** The time series shows trends, seasonality, and non-stationarity. Seasonal decomposition (additive and multiplicative models) identified components, and a de-seasonalized version was plotted.

**3. Stationarity and Differencing** Stationarity was confirmed using the Augmented Dickey-Fuller test and autocorrelation functions. Seasonal differencing with a 12-month lag (D=1) sufficiently stabilized the series.

**4. SARIMA Modeling** SARIMA parameters were optimized using auto_arima. The best model was SARIMA(0,0,0)(0,1,0)[12], which mainly captured seasonal differencing. Forecasts were plotted with confidence intervals, showing trends but limited complexity.

**5. Machine Learning Approach** A Random Forest model was trained on lagged sales features (x_1 to x_12). The Mean Absolute Percentage Error (MAPE) for 1-month horizon predictions was 0.16, reduced to 0.15 with additional rolling and exponential moving average features.

**6. Feature Importance** The most important features for the Random Forest were the latest lag (x_12) and short-term averages (e.g., ma_2). Feature engineering proved crucial for capturing trends.

**7. Out-of-Sample Forecasting** A Random Forest model was trained for each prediction horizon, comparing its MAPE with SARIMA. Machine learning models improved out-of-sample forecasts compared to SARIMA's static seasonal predictions.
