# Index Seasonality Testing


Benjamin Karlsberg


## Intention: 


Explore the data of the past 20 years of the Dow Jones Industrial Average (DJI), S&P 500 (GSPC), and NASDAQ Composite (IXIC) indices and test for monthly trend outliers.


## Motivation:

<!-- #region -->
**To test some of the most commonly known phrases and effects that defy the "Efficient Market Hypothesis"**

**The Efficient Market Hypothesis: Stock prices always trade at their fair market value and all information to be known is reflected in the price. One cannot beat the market.**

Examples:

+ "The January Effect": The seasonal tendency for stocks to rise in January. Theory: Investors sell in December to incur year-end capital gains taxes and reinvest the funds in January.


+ "Sell in May and Go Away": Stocks tend to underperform from May to October. Reasoning being that investors go on vacation during summer.


+ "The Halloween Strategy": The seasonal tendency for stocks rising from Oct. 31 to May 1. Overlaps with "Sell in May and Go Away."


+ "Santa Claus Rally": The seasonal tendency for stocks to rise in the last week of December. People are happier and more optimistic on Christmas! Also, taxes.
<!-- #endregion -->

## Background

<!-- #region -->
The Dow Jones Industrial Average ("The Dow"), NASDAQ Composite, and S&P 500 are the three most-followed indices in US stock markets. Together, these indices are commonly used to valuate the U.S. stock market as a whole.

+ The Dow Jones Industrial Average consists of 30 of the largest cap stocks listed on U.S. stock exchanges


+ The NASDAQ Composite tracks all of the companies listed on the NASDAQ market as a whole and is heavily weighted toward information technology companies (tech).


+ The S&P 500 overlaps with the Dow Jones, consisting of the top 500 large-cap companies listed across all U.S. stock exchanges.
<!-- #endregion -->

## Source:


20 Year Datasets came from Yahoo Finance
+ [Dow Jones Index](https://finance.yahoo.com/quote/%5EDJI/history?period1=946684800&period2=1586390400&interval=1d&filter=history&frequency=1d)

+ [S&P 500 Index](https://finance.yahoo.com/quote/%5EGSPC/history?period1=946684800&period2=1586390400&interval=1d&filter=history&frequency=1d)

+ [NASDAQ Composite](https://finance.yahoo.com/quote/%5EIXIC/history?period1=946684800&period2=1586476800&interval=1d&filter=history&frequency=1d)

```python

```
