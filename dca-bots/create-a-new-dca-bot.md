---
description: This page describes how to create a new DCA bot and explains all the settings.
---

# Create a New DCA Bot

Go to the DCA bots [page](https://mizar.ai/dashboard/trading/dca-bot) and click on the 'Create new bot' button.

### General Settings

In the general settings you can enter a **name** for your bot and provide a **description** for your bot.

{% hint style="info" %}
The name and the description will be shared with other users, if the bot is made public.
{% endhint %}

![](../.gitbook/assets/screenshot-2021-09-15-at-13.18.08.png)

### Strategy Settings

In the strategy Settings section, you can set the high-level behaviors of your bot.

![Strategy Settings](../.gitbook/assets/screen-shot-2021-09-15-at-11.04.56-am.png)

#### Type

The bot can be of two different types: long or short. A Long bot takes long positions which means that it buys and then sells in order to generate profits. Instead, a short bot is a bot that sells and then buys in order to generate profits.

{% hint style="info" %}
Bots can only go short if the bot is trading in the futures market. If the bot is trading in the spot market it can only go long.
{% endhint %}

#### Order Size

Order Size indicates the size of the start order of the position. It is always defined in quote asset. For example, if the bot is trading BTC/USDT the size is expressed in USDT.

#### Safety Order Size

Safety Order Size is the size of the orders that get executed when the price goes against the position taken \(e.g. the position is long and the price goes down\).

#### Start Order Type

There are two types of start order: Market and Limit. When Market type is selected the start order will be executed as market order. Instead when Limit type is selected the start order will be executed with a special aggressive limit order strategy that will avoid price slippage.

#### Start Order Conditions

Start order conditions define the conditions to open a new position.

* **Open Position ASAP:** open a new position as soon as possible.
* **API**: open a new position through an API command.
* **TradingView \(webhook/API\)**: open a new position through TradingView's custom signal.
* **TradingView Indicators**: open a new position based on technical indicators from TradingView, which can be customised directly in Mizar.

### Exchanges and Market

Exchanges and Market section define where your bot will trade.

![Exchanges and Market](../.gitbook/assets/screen-shot-2021-09-15-at-11.46.08-am.png)

Multiple exchanges can be assigned to a bot settings. Only when the bot is activated, then you will be asked to decide in which exchange to run your DCA bot.

Each bot setting can be assigned either to SPOT or FUTURES market.

### Pairs

In the pairs section you can select which pairs to trade. You have to select at least one and you can select as many pairs as you want.

![](../.gitbook/assets/screenshot-2021-09-15-at-13.19.00.png)

### Take Profits

In the take profits section, you can set the the take profit conditions.

![](../.gitbook/assets/screenshot-2021-09-15-at-13.19.18.png)

* **Take Profits:** The percentage a which profit will be taken \(e.g. 1%\).
* **Take Profits Type:** There are two take profits type: either as percentage of the base order or as percentage of total volumes. If you select as **percentage of the base order**, then the take profit percentage will only be applied on the initial base order. For example if the base order size is 100 USD and the take profit percentage is 5%, then the bot will take profit when 5 USD profits can be realised. If multiple safety orders are hit in the same position, then the take profit order is recalculated in such a way that when it hits 5 USD profits will be made. If you select as **percentage of total volumes**, then the take profit percentage is applied on the total size of your position, i.e. base order including all hit safety orders.
* **Trailing Take Profit / Trailing Deviation \(Optional\):** _****_Optionally, it is also possible to activate trailing take profits. In this case when the take profit target has been hit, the position will not be closed immediately. The bot will track the position with a deviation percentage, for example, when the take profit percentage is 5% and the trailing deviation is 0.5%, then the bot trails the position at 4.5% profits. If the profits keep increasing, then the trailing profit target increases as well, but if the profits decrease then the trailing profit stands until the trailing take profit target is hit. The goal of trailing take profit is to maximise the position's profit and capture big price movements without taking profits too early.

{% hint style="info" %}
For trailing take profit to work well, the trailing deviation needs to be set sufficiently large. Otherwise you will still risk taking profits too early.
{% endhint %}

### Stop Loss

![](../.gitbook/assets/screenshot-2021-09-15-at-13.39.25.png)

### Orders Settings

![](../.gitbook/assets/screenshot-2021-09-15-at-13.20.18.png)

### Advanced Settings

![](../.gitbook/assets/screenshot-2021-09-15-at-13.20.37.png)

