---
description: TradingView webhook commands
---

# DCA Bot - TradingView

Endpoint: [https://api.mizar.com/api/v1/dca-bots/trading-view/execute-command](https://api.mizar.com/redoc#tag/DCA-Bot/operation/execute\_command\_api\_v1\_dca\_bots\_trading\_view\_execute\_command\_post)

## Open position

```javascript
{
   "bot_id": "1",
   "action": "open-position",
   "base_asset": "BTC",
   "quote_asset": "USDT",
   "api_key": "<API KEY>"
}
```

## Close position

```javascript
{
   "bot_id": "1",
   "action": "close-position",
   "base_asset": "BTC",
   "quote_asset": "USDT",
   "api_key": "<API KEY>"
}
```

## Close all positions

```javascript
{
   "bot_id": "1",
   "action": "close-all-positions",
   "api_key": "<API KEY>"
}
```

## Stop bot and close all positions

```javascript
{
   "bot_id": "1",
   "action":  "stop-bot-and-close-all-positions",
   "api_key": "<API KEY>"
}
```
