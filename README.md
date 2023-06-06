# Store sale - Time Series Forecast

## Table of contents
* Introduction
* Dataset Description
* Exploratory Data Analysis
* Modeling
* Conclusion

## Introduction

Forecasts aren’t just for meteorologists. Governments forecast economic growth. Scientists attempt to predict the future population. And businesses forecast product demand—a common task of professional data scientists. Forecasts are especially relevant to brick-and-mortar grocery stores, which must dance delicately with how much inventory to buy. Predict a little over, and grocers are stuck with overstocked, perishable goods. Guess a little under, and popular items quickly sell out, leading to lost revenue and upset customers. More accurate forecasting, thanks to machine learning, could help ensure retailers please customers by having just enough of the right products at the right time.
Current subjective forecasting methods for retail have little data to back them up and are unlikely to be automated. The problem becomes even more complex as retailers add new locations with unique needs, new products, ever-transitioning seasonal tastes, and unpredictable product marketing.For grocery stores, more accurate forecasting can decrease food waste related to overstocking and improve customer satisfaction. The results of this ongoing competition, over time, might even ensure your local store has exactly what you need the next time you shop.
In this project, I will predict sales for the thousands of product families sold at Favorita stores located in Ecuador. The training data includes dates, store and product information, whether that item was being promoted, as well as the sales numbers. Additional files include supplementary information that may be useful in building your models.

## Dataset Description

train.csv
* The training data, comprising time series of features **store_nbr**, **family**, and **onpromotion** as well as the target **sales**.
* **store_nbr** identifies the store at which the products are sold.
* **family** identifies the type of product sold.
* **sales** gives the total sales for a product family at a particular store at a given date. Fractional values are possible since products can be sold in fractional units (1.5 kg of cheese, for instance, as opposed to 1 bag of chips).
* **onpromotion** gives the total number of items in a product family that were being promoted at a store at a given date.

test.csv
* The test data, having the same features as the training data. I will predict the target sales for the dates in this file.
* The dates in the test data are for the 15 days after the last date in the training data.

sample_submission.csv
* A sample submission file in the correct format.

stores.csv
* Store metadata, including city, state, type, and cluster.
* cluster is a grouping of similar stores.

oil.csv
* Daily oil price. Includes values during both the train and test data timeframes. (Ecuador is an oil-dependent country and it's economical health is highly vulnerable to shocks in oil prices.)

## Exploratory Data Analysis
* Transactions
There is a stable pattern in Transaction. All months are similar except December from 2013 to 2017 by boxplot. In addition, we've just seen same pattern for each store in previous plot. Store sales had always increased at the end of the year. Transactions increase in spring and decrease after spring.

<img width="878" alt="Screen Shot 2023-06-05 at 6 55 28 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/6aa411f8-4e66-4c30-a6ac-38ca8f706223">

<img width="894" alt="Screen Shot 2023-06-05 at 6 57 28 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/9e686296-87e9-45d6-b1c8-7fb234d5c408">

<img width="895" alt="Screen Shot 2023-06-05 at 6 58 45 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/1e7babc9-51c6-4526-8afb-c9a84a4f2189">

there is a highly correlation between total sales and transactions also.

<img width="841" alt="Screen Shot 2023-06-05 at 11 18 37 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/73ce7363-c9ab-4279-8826-62146a15341d">

Stores make more transactions at weekends. Almost, the patterns are same from 2013 to 2017 and Saturday is the most important day for shopping.

<img width="896" alt="Screen Shot 2023-06-05 at 11 22 47 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/61613d5f-cabd-4fa1-a026-e699853440b6">

* Oil data

  * Linear Interpolation for oil data

<img width="900" alt="Screen Shot 2023-06-05 at 11 26 14 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/ffb237cf-3be2-4c00-985a-ee779892c3cd">

  * The correlation with Daily Oil Prices for sales and transactions. 
  
The correlation values are not strong but the sign of sales is negative. We can imagine that if daily oil price is high, we expect that the Ecuador's economy is bad and it means the price of product increases and sales decreases. There is a negative relationship here.

<img width="898" alt="Screen Shot 2023-06-05 at 11 28 37 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/c454bcda-f3c5-4ece-8357-a4d4784f8508">

* Sales data

  * Store difference 

Most of the stores are similar to each other, when we examine them with correlation matrix. Some stores, such as 20, 21, 22, and 52 may be a little different.

<img width="895" alt="Screen Shot 2023-06-05 at 11 37 41 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/9d654d12-f258-4ad8-b8e9-7ffa73ddbe30">

  * which product family sells much more?

<img width="891" alt="Screen Shot 2023-06-05 at 11 43 06 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/bdde9cdb-381e-4916-afb8-4dc083ab499d">

  * How different can stores be from each other? The plot shows the patten of stores from different cities.

<img width="889" alt="Screen Shot 2023-06-05 at 11 45 25 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/e04795f6-38f0-4c9b-8e21-5e28e731d02b">

* Forecast and Visualization

Linear regression is widely used in practice and adapts naturally to even complex forecasting tasks. The linear regression algorithm learns how to make a weighted sum from its input features.

<img width="914" alt="Screen Shot 2023-06-05 at 11 48 37 PM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/1197c137-5b6d-4608-9c15-ccf9f00358b0">

* Lag features

To make a lag feature we shift the observations of the target series so that they appear to have occured later in time. Here we've created a 1-step lag feature, though shifting by multiple steps is possible too

The plots with 'lag' feature:

<img width="904" alt="Screen Shot 2023-06-06 at 12 00 04 AM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/c0042958-0a9c-4ca2-885f-01a4fcbae042">

The trend component of a time series represents a persistent, long-term change in the mean of the series. The trend is the slowest-moving part of a series, the part representing the largest time scale of importance. In a time series of product sales, an increasing trend might be the effect of a market expansion as more people become aware of the product year by year.

To see what kind of trend a time series might have, we can use a moving average plot. To compute a moving average of a time series, we compute the average of the values within a sliding window of some defined width. Each point on the graph represents the average of all the values in the series that fall within the window on either side. The idea is to smooth out any short-term fluctuations in the series so that only long-term changes remain.

<img width="920" alt="Screen Shot 2023-06-06 at 12 03 01 AM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/f6529638-aa88-4fdc-ba86-cc0b76bbc074">

## Modeling

### Linear regression

<img width="932" alt="Screen Shot 2023-06-06 at 12 04 49 AM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/444ac804-ddfb-4efb-8f1b-eda87c6c6178">

### XGBoost

Linear regression excels at extrapolating trends, but can't learn interactions. XGBoost excels at learning interactions, but can't extrapolate trends. Here we'll learn how to create "hybrid" forecasters that combine complementary learning algorithms and let the strengths of one make up for the weakness of the other.

<img width="603" alt="Screen Shot 2023-06-06 at 12 10 43 AM" src="https://github.com/carriexu111/capstone-project-3/assets/115129335/ea0a4c80-c332-444c-beeb-83aca231c092">

### Deep Learning Multivariate RNN / LSTM Network

I use the Adam optimazation method since it is widely used and performs much better than regular gradient descent.

## Conclusion
* Store sales had always increased at the end of the year.
* There are somewhat correlation with Daily Oil Prices for sales and transactions. 
* GROCERY I and BEVERAGES are the top selling families.
* XGBoost forcast for time series has better result than linear regression. 



