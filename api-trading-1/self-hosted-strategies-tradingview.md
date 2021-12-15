---
description: TradingView webhook commands
---

# API Trading - TradingView

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
  "size": "1"
}
```

{% hint style="info" %}
size indicates the relative size of the position. If you are sure that the position will bring profit use 1, otherwise scale down the size to reduce risks.
{% endhint %}

## Open short position

```javascript
{
  "api_key": "",
  "action": "open-position",
  "strategy_id": "",
  "base_asset": "BTC",
  "quote_asset":"USDT",
  "is_long": "false",
  "size": "1"
}
```

## Close position

```javascript
{
  "api_key": "",
  "action": "close-position",
  "strategy_id": "",
  "position_id": ""
}
```

## Close all open positions

```javascript
{
  "api_key": "",
  "action": "close-all-positions",
  "strategy_id": ""
}
```



## Close all open positions for a specific pair

```javascript
{
  "api_key": "",
  "action": "close-all-positions",
  "strategy_id": "",
  "base_asset": "",
  "quote_asset": ""
}
```
