# Forecasting Volatility 
Comparing the performance of the GARCH(1,1) model and historical volatility, close-to-close volatility, Parkinson volatility, Garman-Klass volatility and Rogers-Satchell volatility in the rolling window method to forecast future volatility on the Nasdaq composite.

Volatility exhibits serial correlation. Future volatility over some period of time is correlated to volatility over the previous period of time when both periods of time are the same. This is the basis on which the rolling window method for forecasting future volatility is built. Here the rolling window method is used to forecast future volatility and different estimators are used to estimate true volatility. Comparisons are then made in the performance of the different estimators. This is repeated for various forecast periods.

Going into this, I expect the close-to-close method to perform the best in the rolling window method. Despite its low efficiency it is an unbiased estimator of true volatility whereas the Parkinson and Garmana-Klass estimators are biased. The Rogers-Satchell estimator is unbiased, however it performs badly when there are gaps. Future investigations on cryptocurrencies would be interesting as these rarely have gaps.

# Performance
The GARCH(1,1) model performed very badly in forecasting volatility. The NASDAQ data was split into a training set to estimate the parameters for the model using the MLE method, and then tested on a training set. The R squared was -1.5! Causes for such a bad R squared are
- A bug. I need to go through my code and make sure there are no errors
- Poor model assumptions. We are assuming the parameteers for the model are constant over 22 years. This is not a good assumption to be making. It may be best to use a rolling window ot estimate the parameters for the model
- Non-optimal forecast period. I only tested the model forecasting volatility over the next 20 days. Is there a better period that the GARCH model works for? If so, why is this true?

The rolling window method performed best when forecasting volatility over the next 10 days. For more days than this, performance declinde and was particularly poor when using periods over 100 days. Below are the R squared statistics for the rolling window method when forecasting over various periods of time

<img width="949" alt="Screenshot 2022-09-28 at 13 36 31" src="https://user-images.githubusercontent.com/108612856/192780165-63a291d9-a99b-4004-b8ec-f09f7d517782.png">
