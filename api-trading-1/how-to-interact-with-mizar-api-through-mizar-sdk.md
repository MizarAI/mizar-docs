---
description: >-
  Here we describe how to create a new self-hosted strategy, open and close
  positions using the Mizar python SDK
---

# API Trading SDK

Self-hosted strategies are strategies hosted by quants/trading firms on their own servers. 

## Creating a new self-hosted strategy

Install the Mizar [client](https://github.com/MizarAI/mizar) and follow the instruction below.

```python
from mizar import Mizar

mizar_client = Mizar()

mizar_client.create_self_hosted_strategy(
    name="My Strategy",
    description="My Strategy works this way",
    exchanges=["binance"],
    symbols=["BTCUSDT"],
    market="SPOT"
)

```

The strategy creation returns a dictionary with the following format

```python
{
     'creation_timestamp': 1625571350830,
     'exchange': 'binance',
     'market': 'SPOT',
     'name': 'My Strategy',
     'strategy_id': 1,
     'symbols': [
         {
             'base_asset': 'BTC',
             'quote_asset': 'USDT',
             'symbol': 'BTCUSDT'
         }
     ]
 }

```

{% hint style="info" %}
 strategy\_id is a unique identifier for your strategy which is used to open and close positions.
{% endhint %}

## Open a position

Open a new position using the `open_position` method 

```python
mizar_client.open_position(
    strategy_id=1,
    base_asset="BTC",
    quote_asset="USDT",
    size=0.3,
    is_long=True
)
```

{% hint style="info" %}
size indicates the relative size of the position. If you are sure that the position will bring profit use 1, otherwise scale down the size to reduce risks.
{% endhint %}

If the position opening is successful it will return a dictionary with the following format

```python
{
     'base_asset': 'BTC',
     'is_long': True,
     'open_price': '34209.480000000000',
     'open_timestamp': 1625572116854,
     'position_id': '1',
     'quote_asset': 'USDT',
     'size': 0.3,
     'strategy_id': '1'
}
```

## Close a position

Close an existing open position using the `close_position` method 

```python
mizar_client.close_position(
    position_id=1
)
```

If the position is closed successfully you will receive

```python
{
     'base_asset': 'BTC',
     'close_price': '33914.640000000000',
     'close_timestamp': 1625572999043,
     'is_long': True,
     'open_price': '33914.640000000000',
     'open_timestamp': 1625572973963,
     'position_id': '1',
     'quote_asset': 'USDT',
     'size': 0.3,
     'strategy_id': '1'
}
```

## List all open positions

Get all the open positions using `get_all_open_positions` method

```python
mizar_client.get_all_open_positions(
    strategy_id=1
)
```

Will return 

```python
{'open_positions': [
    { 
        'base_asset': 'BTC',
        'is_long': True,
        'open_price': '33871.070000000000',
        'open_timestamp': 1625573293041,
        'position_id': '1',
        'quote_asset': 'USDT',
        'size': 1.0,
        'strategy_id': '1'
     },
     {
        'base_asset': 'BTC',
        'is_long': True,
        'open_price': '33871.070000000000',
        'open_timestamp': 1625573294312,
        'position_id': '2',
        'quote_asset': 'USDT',
        'size': 1.0,
        'strategy_id': '1'
     },
     {  
        'base_asset': 'BTC',
        'is_long': True,
        'open_price': '33871.070000000000',
        'open_timestamp': 1625573295016,
        'position_id': '3',
        'quote_asset': 'USDT',
        'size': 1.0,
        'strategy_id': '1'
     }
  ]
}

```

## Close all open positions

Close all the positions using `close_all_positions` method

```python
mizar_client.get_all_open_positions(
    strategy_id=1
)
```

Will return

```python
{'closed_positions': [
     {
        'base_asset': 'BTC',
        'close_price': '34146.340000000000',
        'close_timestamp': 1625574840982,
        'is_long': True,
        'open_price': '33871.070000000000',
        'open_timestamp': 1625573293041,
        'position_id': '1',
        'quote_asset': 'USDT',
        'size': 1.0,
        'strategy_id': '`'
     },
     { 
        'base_asset': 'BTC',
        'close_price': '34146.340000000000',
        'close_timestamp': 1625574841018,
        'is_long': True,
        'open_price': '33871.070000000000',
        'open_timestamp': 1625573294312,
        'position_id': '2',
        'quote_asset': 'USDT',
        'size': 1.0,
        'strategy_id': '1'
     },
     {'base_asset': 'BTC',
      'close_price': '34146.340000000000',
      'close_timestamp': 1625574841045,
      'is_long': True,
      'open_price': '33871.070000000000',
      'open_timestamp': 1625573295016,
      'position_id': '3',
      'quote_asset': 'USDT',
      'size': 1.0,
      'strategy_id': '1'
      }
   ]
}
```

