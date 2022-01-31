---
description: >-
  Users can copy other traders and perform as they do. In exchange, copied
  traders are rewarded based on their realized monthly profits.
---

# Performance Fee

Traders can share successful strategies via the marketplace and get copied by other investors. In this way, traders are rewarded for their performance, while other investors can benefit from copying them. Traders are free to propose their own performance fee, which is shown in the strategy general information.

When copying another trader, the investor will have to pay a performance fee based on the gross realized profit or loss. This is reconciled and automatically withdrawn (when realized daily profit) or credited (when realized daily losses and amount to be credited does not exceed the amount withdrawn) from the Mizar wallet every 24 hours.

{% hint style="info" %}
IMPORTANT: over a calendar month, the total performance fee for a strategy cannot be negative. In case of loss, no performance fee will applied for that month.
{% endhint %}

{% hint style="info" %}
IMPORTANT: The performance fee is calculated on closed positions only. Unrealized Profit or Loss are not taken into account in the performance fee.&#x20;
{% endhint %}

{% hint style="info" %}
Check [here](../star-program-fees-reduction.md) to know more about the Mizar fee structure and how the performance fee can be reduced.
{% endhint %}

#### Example (profit):

1. Trader A follows Trader B and copy-trade her strategy. The performance fee applied from Trader B is 10%. At the end of the second day of August, Trader A performs a total gross profit (i.e. no volume fee or exchange fees applied) of $200, with STAR level of Trader A is "White Dwarf", which gives Trader A, no discount on his performance fee. At the end of the day, Trader A pays the following performance fee: $200 \* 10% = $20.
2. At the end of the second day of August, Trader A performs a total gross profit of +$500, with "Sub Giant" as STAR level (10% discount on performance fee). At the end of the day, Trader A pays the following performance fee: $500 \* 10%\* (100%-10%) = $45
3. The strategy does not open any other position until the end of the month. The total Profits and Loss at the end of the month is of +$700 and the user paid a total performance fee of $65 (9.2%).

#### Example (loss):

1. Trader A follows Trader B and copy-trade her strategy. The performance fee applied from Trader B is 5%. During the first day of August, Trader A performs a total gross profit of +$2,000, with "Hyper Giant" as STAR level (50% discount on performance fee). At the end of the day, Trader A pays the following performance fee: +$2,000 \* 5% \* 50%= $50
2. During the second day of August, Trader A performs a total gross loss of -$500, with "Hyper Giant" as STAR level. Trader A is refunded as following: -$500 \* 5% \* 50%= -$12.5. The cumulated performance fee paid over the calendar month of August is $50-$12.5=$37.5, while the cumulated gross profits are $1,500.
3. During the third day of August, Trader A performs a total gross loss of -$2,500, with "Hyper Giant" as STAR level. Trader A is refunded of $37.5 (the cumulated performance fee paid until that day) and the remaining $25 ($37.5 - $2,500 \* 5% \* 50% = $25) are accounted and usable to discount the performance fee over the next days, until the end of the month.&#x20;
4. Scenarios:
   1. The strategy does not open any other position until the end of the month. The loss is of -$1,000, the user does not pay any performance fee.
   2. The strategy opens a new position and performs a profit of +$1,500, with "Hyper Giant" as STAR level. At the end of the day, Trader A pays the following performance fee: +$2,000 \* 5% \* 50% - $25= $25. The monthly profit is +$500 and Trader A pays a total of $25 (5%).

{% hint style="info" %}
IMPORTANT: If the users have no available balance in their Mizar wallet, the bots could run in a limited bot and positions could not be opened. Always make sure to have enough balance to avoid bots running in limited mode
{% endhint %}
