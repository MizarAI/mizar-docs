---
description: On Mizar, traders pay on how much volumes have been traded on a daily basis.
---

# Volume Fee



With Mizar, users pay a daily volume fee based on how much volume has been traded in that day. The volume fee is detracted each day from the user Mizar wallet.

Mizar applies max 0.06% trading fee on each dollar traded.&#x20;

{% hint style="info" %}
Check [here](../star-program-fees-reduction.md) to know more about the Mizar fee structure and how the volume fee can be reduced.
{% endhint %}

#### Examples:

1. Trader A has one active subscription. In total, the bot trades, in one day, $3,000 of volume. Trader A has right to $10,000 free volumes. For this reason, no fee is applied. Trader A has still $7,000 free volume to be used until the end of the current calendar month.
2. Trader B has 5 active subscriptions. In total, the bots trade, in one day, $56,000 of volume. Trader B has right to $10,000 free volume to be used in the current calendar month. In that day, the STAR level of Trader B is "White Dwarf", which implies a fee of 0.06% applied to each traded volume. Mizar applies the following volume fee: ($56,000 - $10,000) \* 0.06% = $27.6. Trader B has no free volume left until the first day of the following calendar month.
3. Trader C has 15 active subscriptions. In total, the bots trade, in one day, $500,000 of volume. In that day, the STAR level of Trader C is "Hyper Giant", which implies a fee of 0.01% applied to each traded volume. Trader C is an early adopter and has right to $100,000 free volume to be used in the current calendar month. Mizar applies the following fee: ($500,000 - $100,000) \* 0.01% = $40. Trader C has no free volume left until the first day of the following calendar month.

{% hint style="info" %}
IMPORTANT: If the users have no available balance in their Mizar wallet nor free volume left, the bots could run in a limited bot and positions could not be opened. Always make sure to have enough balance or free volume to avoid bots running in limited mode. If the wallet is out of capital, the open positions will be closed according to the strategy.
{% endhint %}
