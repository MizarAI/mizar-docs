---
description: >-
  Release your strategy on Mizar and leverage its infrastructure, so that quants
  only have to focus on developing their model.
---

# Strategy Deployment

Building a trading strategy costs a lot of effort, but building an entire trading system costs even more effort. A quant can save a lot of time and effort by making use of the services that Mizar has to offer. The Mizar live trading system consists of various parts described below and is available to all our users who deploy their strategy on the platform.

**Live Ingestion and Transformation**

The data sources used to create targets and labels need to be ingested continuously and stored in databases. The more markets you trade simultaneously, the more data you have to ingest as well. It is therefore important that your trading system can scale horizontally with the number of markets you wish to trade and the amount of data sources you wish to ingest.

The backend of Mizar is continuously ingesting tick data from multiple markets and other data sources and transforming this data such that it is ready to use machine learning models. For example, tick data is aggregated into candlestick bars, which are then transformed into moving averages which can then be fed into a machine learning model that uses moving averages as features. 

**Live Prediction**

A model that is trading live needs to be continuously fed with data in order to make predictions. These models need to be continuously running such that actions can be taken as soon as possible when models predict to take a position.

**Trade Execution**

When a model predicts to take a position, it is important to execute the trade as soon as possible. When executing a trade it is important to take into account the order book and determine what the slippage is, such that the trade can be executed as optimal as possible.

**Trade Monitoring**

Positions that have been opened by the model have to be monitored, for example when a long position is opened, then the position should be closed if either the stop-loss of profit-taking levels are hit. Or if the price goes sideways and there is no clear trend, then the position should be closed after some pre-defined time set by the user to prevent having the position opened indefinitely.



