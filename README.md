# Pharma Sales Data Forecasting
The sales forecasting in pharmaceutical industry is typically done by using Naïve model, where the forecasted values equal values in the previous period with added factor of growth, which is specifically defined for different regions, markets, categories of products, etc. Although this model fails when the market saturates, in general and on a larger scale, it has proven as successful. Still, analysis and forecasts on a smaller scale, such as single distributor, pharmacy chain or even individual pharmacy, smaller periods such as weeks, etc., guide very important decisions related to resource and procurement planning, what-if analyses, return-on-investment forecasting, business planning and others.

Thus, the main objective of this project is to tackle the exploration of the feasibility of the usage of modern time-series forecasting methods in pharmaceutical products sales forecasting on a smaller scale.

#### -- Project Status: [Completed]

## Project Intro/Objective
The objective of the project is to validate different methods and approaches related to sales time series data preparation, analysis and forecasting. With aim to facilitate recommending sales and marketing strategies based on trend/seasonality effects and forecasting sales of eight different groups of pharmaceutical products with diverse characteristics, such as stationarity, seasonality, amount of residuals and sales data variance. Effectiveness of three forecasting methods, namely ARIMA, Facebook’s Prophet and Long-Short Term Memory (LSTM) neural networks is investigated. Each of the method is complemented with two optimization and validation approaches, relevant for short-term (so called rolling forecast scenario) and long-term forecasting.

### Methods Used
* Inferential Statistics
* Time series Analysis
* Deep Learning - LSTMs
* Ensemble Learning
* Data Visualization
* Predictive Modeling

### Technologies
* Python
* Plotly, Seaborn, Matlplotlib
* Pandas, jupyter
* ARIMA, Prophet, LSTM


## Project Description
Initial dataset consisted of 600000 transactional data collected in 6 years (period 2014-2019), indicating date and time of sale, pharmaceutical drug brand name and sold quantity. As a result of the interviews with pharmacists, decision was made that the subject of analyses and forecasting will be actual drug categories, instead of the individual drugs. Thus, selected group of drugs (57 drugs) is classified to 8 Anatomical Therapeutic Chemical (ATC) Classification System categories:

M01AB - Anti-inflammatory and antirheumatic products, non-steroids, Acetic acid derivatives and related substances
M01AE - Anti-inflammatory and antirheumatic products, non-steroids, Propionic acid derivatives
N02BA - Other analgesics and antipyretics, Salicylic acid and derivatives
N02BE/B - Other analgesics and antipyretics, Pyrazolones and Anilides
N05B - Psycholeptics drugs, Anxiolytic drugs
N05C - Psycholeptics drugs, Hypnotics and sedatives drugs
R03 - Drugs for obstructive airway diseases
R06 - Antihistamines for systemic use

Stationarity of time-series is the property of exhibiting constant statistical properties over time (for example, mean, variance, autocorrelation). It can be visually determined by plotting rolling statistics (rolling means and variances). In stationary time series, the mean of the series, variance of the series and covariance of the i th term and the (i + m) th term should not be a function of time.

![alt text](https://github.com/AlpeshPatil34/Pharma-Sales-Data-Forecasting/blob/master/images/PACF%20plot.png)
We can use Augmented Dickey-Fuller (ADF) test to check stationarity of the data. Possible values of regression parameters of ADF are:

c : constant only (default)
ct : constant and trend
ctt : constant, and linear and quadratic trend
nc : no constant, no trend
![alt text](https://github.com/AlpeshPatil34/Pharma-Sales-Data-Forecasting/blob/master/images/ACF%20Plot.png)

## Forecasting with Prophet - 
Prophet model is fited with data in two columns, where first one contains time information and is labeled as ds. Another stores actual time series data and is labeled as y.
![alt text](https://github.com/AlpeshPatil34/Pharma-Sales-Data-Forecasting/blob/master/images/Prophet.png)

## Forecasting with LSTM - 
Long-term forecasting validation has been done with three LSTM configurations: Vanilla LSTM, Stacked LSTM and Bi-directional LSTM. Relu activation function was used, optimizer was Adam and loss function was Mean Squared Error. The best results were achieved with training the model in 400 epochs. Before fitting, all data was standardized (rescaled in interval -1,1) and transformed to data for supervised problem.

Number of past observations tested in input sequences was either 10 or 5. For series with larger variances and randomness (N05B and N05C) and simpler, Vanilla LSTM model, 10 past observations produced better forecasting accuracy. In all other cases, 5 past observations were used. This is the parameter that has been adopted.
![alt text](https://github.com/AlpeshPatil34/Pharma-Sales-Data-Forecasting/blob/master/images/Stacked%20LSTM.png)


## Newer Applications - 
Newer packages such as Greykite, Kats & many other SOTA developments can be applied for a better production model.
