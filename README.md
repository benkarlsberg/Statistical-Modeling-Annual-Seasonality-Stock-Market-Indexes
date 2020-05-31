# Index Seasonality Testing


Benjamin Karlsberg


## Description: 


Exploring the data of the past 20 years (2000-01-01 to 2019-12-31) of the Dow Jones Industrial Average (DJI), S&P 500 (GSPC), and NASDAQ Composite (IXIC) indices and test for monthly and seasonal trend outliers.


## Motivation:

<!-- #region -->
**To test some of the most commonly known phrases and effects that defy the "Efficient Market Hypothesis"**

**The Efficient Market Hypothesis: Stock prices always trade at their fair market value and all information to be known is reflected in the price. One cannot time the market.**

Examples:

+ "The January Effect": The seasonal tendency for stocks to rise in January. Theory: Investors sell in December to incur year-end capital gains taxes and reinvest the funds in January.


+ "Sell in May and Go Away": Stocks tend to underperform from May to October. Reasoning being that investors go on vacation during summer.


+ "The Halloween Strategy": The seasonal tendency for stocks rising from Oct. 31 to May 1. Overlaps with "Sell in May and Go Away."


+ "Santa Claus Rally": The seasonal tendency for stocks to rise in the last week of December. People are happier and more optimistic on Christmas! Also, taxes.
<!-- #endregion -->

## Background

<!-- #region -->
The Dow Jones Industrial Average ("The Dow"), NASDAQ Composite, and S&P 500 are the three most-followed indices in US stock market. Together, these indices are commonly used to valuate the U.S. stock market as a whole.

+ The Dow Jones Industrial Average consists of 30 of the largest cap stocks listed on U.S. stock exchanges


+ The NASDAQ Composite tracks all of the companies listed on the NASDAQ market as a whole (3000 stocks) and is heavily weighted toward information technology companies (tech).


+ The S&P 500 overlaps with the Dow Jones, consisting of the top 500 large-cap companies listed across all U.S. stock exchanges.
<!-- #endregion -->

## Source:


20 Year Datasets came from Yahoo Finance
+ [Dow Jones Index](https://finance.yahoo.com/quote/%5EDJI/history?period1=946684800&period2=1586390400&interval=1d&filter=history&frequency=1d)

+ [S&P 500 Index](https://finance.yahoo.com/quote/%5EGSPC/history?period1=946684800&period2=1586390400&interval=1d&filter=history&frequency=1d)

+ [NASDAQ Composite](https://finance.yahoo.com/quote/%5EIXIC/history?period1=946684800&period2=1586476800&interval=1d&filter=history&frequency=1d)

Columns included:
+ Date
+ Open Price
+ Peak Price
+ Low Price
+ Close Price
+ Adjusted Close Price
+ Volume

Total days counted in each dataset: 5096


## Data Pipeline:

<!-- #region -->
+ The Data was loaded in as a csv file using Pandas library and graphs were plotted using the Matplotlib library


+ It was ordered by date in string format, so I added a column in datetime format using datetime module as well as individual Year and Month columns for grouping purposes


+ A column was added for the difference between the previous day close price and a label column to mark if the difference was positive or negative


+ Using the resample method, I was able to calculate the total increase or decrease in price between each business month over 20 years


+ The observed frequencies of an increase or decrease in price for each month was calculated and plotted for chi-squared testing


+ The average percent change in index price was graphed for each month as a line graph


+ Histograms comparing the percent change in the summer months and winter months was created to be utilized for a t-test comparing the means



<!-- #endregion -->

## 20 Year History:


<img src="images/20 year dji.png">

<img src="images/20 year s&p.png">

<img src="images/20 year nasdaq.png">


## Trend Graphs:


<img src="images/dji average monthly close change.png" width= 800>

<img src="images/nasdaq average monthly close change.png">

<img src="images/s&p average monthly close change.png">


## Hypothesis Tests and Outcomes: 


### Question 1 : Do the stock market indexes show a monthly seasonality trend or are they generally uniformly distributed?

+ Null Hypothesis: The month of the year should not matter for index price so the months should follow a uniform distribution (Efficient Market Hypothesis).

+ Alternate Hypothesis: The month has an effect on the index price.


<!-- #region -->
#### In order to run a Chi-Squared test, I evaluated each month to an increase or decrease in monthly closing price to establish trends as discrete variables. A positive month counts as a success in the following histograms.

#### With a PMF for each month being 1/12 and 240 samples of months, the expected value is assumed to be 10 for each month.
+ Samples are taken from the January, 2000 through December 2019

<img src="images/dji monthly increase freqs.png">


<img src="images/s&p monthly increase freqs.png">


<img src="images/nasdaq monthly increase freqs.png">
<!-- #endregion -->

#### Chi-squared results:

+ DJI p-value for All Months: 0.287

+ S&P 500 p-value for All Months: 0.539

+ NASDAQ Composite p-value for All Months: 0.916


### Question 2: Is there a seasonality difference in index price changes between the Summer and Winter months?


+ Null Hypothesis: The seasonal time of the year should not have a significant effect on the stock market (Efficient Market Hypothesis)

+ Alternate Hypothesis: There is a seasonal difference in stock trends between the Winter (November 1st through April 31st) and Summer (May 1st to Oct 31st) months



<table><tr>
<td> <img src="images/dji summer hist.png" width="500" /> </td>
<td> <img src="images/dji winter hist.png" width="500" /> </td>
<td></table>


<table><tr>
<td> <img src="images/s&p summer hist.png" width="500" /> </td>
<td> <img src="images/s&p winter hist.png" width="500" /> </td>
<td></table>


<table><tr>
<td> <img src="images/nasdaq summer hist.png" width="500" /> </td>
<td> <img src="images/nasdaq winter hist.png" width="500" /> </td>
<td></table>


#### Because these histograms appear to be normally distributed, I chose to use Welch's two-tailed t-test to compare the similarity of the sample means.

<!-- #region -->
#### Welch t-test results:

DJI:
+ Welch Test Statistic: 1.24
+ Degrees of Freedom for Welch's Test: 237.89
+ p-value for different seasons using t-test: 0.22


S&P 500:
+ Welch Test Statistic: 1.13
+ Degrees of Freedom for Welch's Test: 237.96
+ p-value for different seasons using t-test: 0.26


NASDAQ Composite:
+ Welch Test Statistic: 0.14
+ Degrees of Freedom for Welch's Test: 236.35
+ p-value for different seasons: 0.89
<!-- #endregion -->

## Conclusion: 


At first glance, it appears that the trend graphs are showing significant differences in how each month performs on average in terms of percent change. However, when we test the hypotheses that seasonality (between months or seasons of the year) has an effect on index price, we do not see very strong p-values to conclude that seasonality is a major factor in determining stock trends. Therefore, the data generated is more likely to be consistent with seasonality following a uniform distribution.


## Future Direction:

<!-- #region -->
Testing seasonality can be very valuable to a variety different topics. For example, similar methods can be applied to testing the seasonal activity of a virus or bacteria as was done here on the stock market.


This topic proved to be very interesting and I learned a lot about managing time-dependent data. I would like to continue with this project in the future to test for other trends that might exist.
<!-- #endregion -->
