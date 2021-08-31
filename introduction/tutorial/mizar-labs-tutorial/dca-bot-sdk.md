# DCA Bot SDK

Install the Mizar [client](https://github.com/MizarAI/mizar) and follow the instruction below.

## Open Position

```python
from mizar import Mizar

mizar_client = Mizar()

mizar_client.dca_bot_open_position(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT",
)

```

It is allowed to override the take profit and stop loss of the bot for

```python
mizar_client.dca_bot_open_position(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT",
    take_profit=0.05
    stop_loss=0.10
)
```

## Close Position

```python
mizar_client.dca_bot_close_position(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT",
)
```

## Shift Safety Orders

```python
mizar_client.dca_bot_shift_safety_orders(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT",
    safety_orders_start_price=45000
)
```

## Close All Positions

```python
mizar_client.dca_bot_close_positions(
    bot_id=1,
)
```

## Stop Bot and Close all positions

```python
mizar_client.dca_bot_stop_and_close_positions(
    bot_id=1,
)
```

## Get Open Positions

```python
mizar_client.get_dca_bot_position(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT"
)
```

## Get Safety Orders

```python
mizar_client.get_dca_bot_safety_orders(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT"
)
```

## Get Active Safety Orders

```python
mizar_client.get_dca_bot_active_safety_orders(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT"
)
```

## Get Inactive Safety Orders

```python
mizar_client.get_dca_bot_inactive_safety_orders(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT"
)
```

## Get Take Profit Orders

```python
mizar_client.get_dca_bot_take_profit_orders(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT"
)
```

