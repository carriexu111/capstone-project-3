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



