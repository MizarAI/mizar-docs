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

Expected response

```python
{'detail': 
'Request with action open-position has been successfully submitted to bot 1 that has 1 subscriptions.'}
```

## Close Position

```python
mizar_client.dca_bot_close_position(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT",
)
```

Expected response

```python
{'detail': 
'Request with action close-position has been successfully submitted to bot 1 that has 1 subscriptions.'}
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

Expected response

```python
{'detail': 
'Request with action shift-safety-orders has been successfully submitted to bot 1 that has 1 subscriptions.'}
```

## Close All Positions

```python
mizar_client.dca_bot_close_positions(
    bot_id=1,
)
```

Expected response

```python
{'detail': 
'Request with action close-all-positions has been successfully submitted to bot 1 that has 1 subscriptions.'}
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

Expected response

```python
{'data': {'symbol': 'BTCUSDT',
  'start_condition_datetime': '2021-08-31T17:21:02.953815',
  'take_profit_type': 'total',
  'take_profit_pct': 0.01,
  'stop_loss_pct': None,
  'safety_order_deviation_pct': 0.015,
  'safety_order_step_scale': 1.05,
  'safety_order_quote_size': 150.0,
  'safety_order_volume_scale': 1.05,
  'max_num_safety_order': 5,
  'side': 'buy',
  'base_orders': [{'id': '30331250182',
    'status': 'canceled',
    'timestamp': 1630430469415,
    'price': 47415.4,
    'filled': 0.0,
    'remaining': 0.005},
   {'id': '30331253419',
    'status': 'canceled',
    'timestamp': 1630430476596,
    'price': 47418.5,
    'filled': 0.0,
    'remaining': 0.005},
   {'id': '30331257401',
    'status': 'canceled',
    'timestamp': 1630430485760,
    'price': 47418.86,
    'filled': 0.0,
    'remaining': 0.005},
   {'id': '30331263515',
    'status': 'closed',
    'timestamp': 1630430486088,
    'price': 47423.37,
    'filled': 0.005,
    'remaining': 0.0}],
  'active_safety_orders': [{'id': '30331268368',
    'status': 'open',
    'timestamp': 1630430492830,
    'price': 46712.02,
    'filled': 0.0,
    'remaining': 0.003}],
  'take_profit_order': {'id': '30331267657',
   'status': 'open',
   'timestamp': 1630430491891,
   'price': 47897.6,
   'filled': 0.0,
   'remaining': 0.005},
  'inactive_safety_orders': [],
  'inactive_take_profit_orders': []}}

```

## Get Safety Orders

```python
mizar_client.get_dca_bot_safety_orders(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT"
)
```

Expected response

```python
{'data': [{'id': '30331268368',
   'status': 'open',
   'timestamp': 1630430492830,
   'price': 46712.02,
   'filled': 0.0,
   'remaining': 0.003}]}
```

## Get Active Safety Orders

```python
mizar_client.get_dca_bot_active_safety_orders(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT"
)
```

Expected response

```python
{'data': [{'id': '30331268368',
   'status': 'open',
   'timestamp': 1630430492830,
   'price': 46712.02,
   'filled': 0.0,
   'remaining': 0.003}]}
```

## Get Inactive Safety Orders

```python
mizar_client.get_dca_bot_inactive_safety_orders(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT"
)
```

Expected response

```python
{'data': [{'id': '30331268368',
   'status': 'canceled',
   'timestamp': 1630430658612,
   'price': 46712.02,
   'filled': 0.0,
   'remaining': 0.003}]}
```

## Get Take Profit Orders

```python
mizar_client.get_dca_bot_take_profit_orders(
    bot_id=1,
    base_asset="BTC",
    quote_asset="USDT"
)
```

Expected response

```python
{'data': [{'id': '30331268368',
   'status': 'canceled',
   'timestamp': 1630430658612,
   'price': 46712.02,
   'filled': 0.0,
   'remaining': 0.003}]}
```

