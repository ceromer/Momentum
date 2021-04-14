# Momentum Trading

This strategy works with stocks in the S&P 500. By resampling daily prices to month-end prices, the strategy generates trading signal to perform trading once a month.

The primary momentum indicator is the log returns. They are computed using a dataframe and a shift_returns function used to shift the log returns to the previous or future returns in the time series. 

Generating a Trading Signal: for each month-end observation period, rank the stocks by previous returns, from the highest to the lowest. Select the top performing stocks for the long portfolio, and the bottom performing stocks for the short portfolio.

Statistical test: a t-Test is implemented where the null hypothesis (𝐻0) is that the actual mean return from the signal is zero. A one-sample, one-sided t-test on the observed mean return, to see if we can reject 𝐻0. After computing the t-statistic and its corresponding p-value, which will indicate the probability of observing a t-statistic equally or more extreme than the one we observed if the null hypothesis were true. A small p-value means that the chance of observing the t-statistic we observed under the null hypothesis is small, and thus casts doubt on the null hypothesis. As per good practice a desired level of significance or alpha ( 𝛼 ) before computing the p-value, in this case 𝛼=0.05 and then reject the null hypothesis if 𝑝<𝛼.
