---
description: TradingView webhook commands
---

# Self-Hosted Strategies TradingView

## Open long position

```javascript
{
  "api_key": "",
  "action": "open-position",
  "strategy_id": "",
  "base_asset": "BTC",
  "quote_asset":"USDT",
  "is_long": "true"
}
```

## Open short position

```javascript
{
  "api_key": "",
  "action": "open-position",
  "strategy_id": "",
  "base_asset": "BTC",
  "quote_asset":"USDT",
  "is_long": "false"
}
```

## Close position

```javascript
{
  "api_key": "",
  "action": "close-position",
  "strategy_id": "",
  "position_id": "",
}
```

## Close all open positions

```javascript
{
  "api_key": "",
  "action": "close-all-positions",
  "strategy_id": "",
}
```

