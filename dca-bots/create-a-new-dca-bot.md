---
description: This page describes how to create a new DCA bot and explains all the settings.
---

# Create a New DCA Bot

Go to the DCA bots [page](https://mizar.ai/dashboard/trading/dca-bot) and click on the 'Create new bot' button.

### General Settings

In the general settings you can enter a name for your bot and provide a description for your bot. The name and the description will be shared with other users, if the bot is made public.

![General settings](../.gitbook/assets/general_settings.png)

### Strategy Settings

In the strategy Settings section, you can set the high-level behaviours of your bot.

![Strategy Settings](../.gitbook/assets/screen-shot-2021-09-15-at-11.04.56-am.png)

#### Type

The bot can be of two different types: long or short. A Long bot takes long positions which means that it buys and then sells in order to generate profits. Instead, a short bot is a bot that sells and then buys in order to generate profits.

#### Order Size

Order Size indicates the size of the start order of the position. It is always defined in quote asset.

#### Safety Order Size

Safety Order Size is the size of the orders that get executed when the price goes against the position taken \(e.g. the position is long and the price goes down\). The Safety Orders are useful to reduce risks and generate profits with small price movements.

#### Start Order Type

There are two types of start order: Market and LImit. When Market type is selected the start order will be executed as market order. Instead when Limit type is selected the start order will be executed with a special aggressive limit order strategy that will avoid price slippage.





