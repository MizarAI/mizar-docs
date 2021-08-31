---
description: TradingView webhook commands
---

# Self-Hosted Strategies TradingView

Endpoint: [https://api.mizar.ai/api/v1/trading-view/execute-command](https://api.mizar.ai/api/v1/trading-view/execute-command)

## Open long position

```javascript
{
  "api_key": "",
  "action": "open-position",
  "strategy_id": "",
  "base_asset": "BTC",
  "quote_asset":"USDT",
  "is_long": "true",
  "size": "1",
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

