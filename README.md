# consumption-tracking-and-causal-analysis
A pipeline tracking top sector movers based on metrics related to customer consumption to inform potential investment opportunities, identifying top demographic factors of customers correlated to the metric movement, and analyzing structural vs behavioral contribution of representative customer segments to the change. 

## Background
### Mission
Our research team in the company has always been working around behavior chages of people. Such research help us have a better understanding of consumers' behavior shift and investment inspiration and implication behind the change. The earlier we catch those interesting signals, the less type II error in venture decision making we would cause. Good insights includes what sectors are trending differently and what caused that change.

### Dataset
The research team in the company owns a datastream of credit card transaction data synced from the first party. The data includes every single transactions of ~100k consumers and demographic information of them from 2019 to the date. 

## Problem Statement
Given the datastream and all related themes, we would want to leverage this data to identify early signals among various consumption sectors, unfold demographic factors correlated the change the most, and see how much so called constructual and behavioral contribution each segment makes to the change.

<p align="center">
  <img src="/fig/frame.png" style="max-width: 1000px"/>
  <em>Pipeline Frame</em>
</p>

## Pipeline breakdown
### Time Sereis Tracking
Facebook Prophet Time Series Framework is used to fit the historical data, as it is a user-friendly framework, which takes into account trends, seasonality, and holidays automaticalll. There is a list of metrics of our interest treated as measurement of consumer behaviors, including total spending, average spending, visits, conversion and so on.

Each time series model is built on each metric under individual product category. Fitting the historical data, the model will output a projection for specified time window e.g one month. Based on the actual values for the metric and the projection, we design an indicator (consumer impact index or CII) that measures the degree of deviation of the actual values away from the projection such that the higher the indicator score is, the more deviate those actual points are. 

<p align="center">
  <img src="/fig/time_series.png" style="max-width: 1000px"/>
  <em>E.g Time Sereis Tracking on One of Product Categories</em>
</p>

The CII scores will enable us to rank top sector movers as shown below:

<p align="center">
  <img src="/fig/ranking.png" style="max-width: 1000px" width="800"/>
  <em>Secotors Ranked by CII scores </em>
</p>

