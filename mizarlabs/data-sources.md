---
description: What does Mizar have to offer in terms of data sources?
---

# Data Sources

The Mizar platform provides users access to an enormous dataset consisting of various data sources. Data sources are refreshed live and can therefore be used by quants to create predictive features for their models. In the following section, the various data sources will be described.

**Tick Data**

A tick represents a single buy or sell order on an exchange and has the highest level of granularity. The Mizar platform will continuously ingest tick level data from various trading pairs from various exchanges and store this in its data warehouse.

**Candlestick Bars**

Since tick level data has the highest level granularity it can be considered as big data, which might be too detailed and have a low signal-to-noise ratio for developing strategies.  Mizar therefore also aggregates tick data into candlestick bars to enable traders to work with less detailed data. These traditional candlestick bars should be familiar to most quants and easier to work with. 

Mizar allows the creation of strategies with multiple types of candlestick bars:

* Traditional time bars are obtained sampling information at fixed time intervals \(5min, 15min,  30min, 1h, 2h, 4h, 6h, 12h, and 1 day\).
* Volume bars are obtained sampling information at a pre-defined number of exchanged base assets, e.g. a bar is created after 10 BTC has been traded in the BTC/USDT pair.
* Dollar bars are obtained sampling information at a pre-defined number of exchanged quote assets, e.g. a bar is created after 10,000 USDT has been traded in the BTC/USDT pair.
* Tick bars are obtained sampling information at a predefined number of transactions, e.g. a bar is created after every 1,000 ticks.

These volume, dollar, and tick pairs are introduced, because time bars typically suffer from poor statistical properties such as serial correlation, heteroskedasticity \(mixed periods of high or low volatility\), and non-normality of returns \(the distribution of returns is typically skewed and fat-tailed\). In addition, financial markets do not process information at constant time intervals \(in the night there is less trading than during the day\), which implies that time bars oversample information during the night and undersample information during the day.

**On-Chain Data \(Future Development\)**

Algorithmic strategies are often developed using indicators based on pricing and volume data, however, this only takes into consideration a limited amount of information that is available to a large part of the market. During the last years, more and more traders have leveraged public blockchain information to enhance their strategies. In fact, on-chain analysis platforms like [nansen.ai](https://nansen.ai/) and [glassnode.com](https://glassnode.com/) are becoming increasingly popular.

Mizar aims to offer a rich choice of on-chain indicators bringing a unique feature in the algorithmic strategies platform. On-chain data can be transformed into predictive features, for example, wallets of users can be analysed and large transactions to and from exchanges can be used as an indicator to see whether traders with asymmetric information are active.

