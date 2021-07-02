---
description: >-
  Develop and deploy your first trading strategy and take part of the quant
  revolution
---

# Develop and Deploy Your First Strategy

## Select a target pair

If you haven't done yet, create a Mizar API key

First of all, we instantiate MizarStudio. MizarStudio is a simple wrapper over the Mizar API, which allows users to retrieve bar data quickly and efficiently.

```python
from mizar.mizar_studio import MizarStudio

mizar_studio = MizarStudio()

```

Once the pair and bar type are selected and we need to collect its historical data.

```bash
bars_df = mizar_studio.get_historical_data(
    "BTC", 
    "USDT", 
    "binance",
    "time",
    "1d"
)
```

Great! now that the data is available we create the labels based on the triple barrier labeling method accessible from [MizarLabs](https://github.com/MizarAI/mizar-labs)

```bash
from mizarlabs.transformers.targets.labeling import TripleBarrierMethodLabeling

number_expiration_bars = 20
stop_loss_factor = 1.5
profit_taking_factor = 1.5

triple_barrier_transformer = TripleBarrierMethodLabeling(
    number_expiration_bars, profit_taking_factor, stop_loss_factor
)

df_triple_barrier_labels = triple_barrier_transformer.transform(df[["close"]])
```

Finally, we can train our strategy using a simple moving average cross-over strategy. After training the strategy can be published on Mizar where it will be evaluated.

```bash
from mizarlabs.model.pipeline import StrategySignalPipeline
from mizarlabs.transformers.technical.moving_average import MovingAverageCrossOverPredictor

fast_ma = 10
slow_ma = 40

cross_over_strategy = StrategySignalPipeline(
    primary_model=MovingAverageCrossOverPredictor(
        fast_ma, slow_ma, "close", fill_between_crossovers=True
    ),
    feature_transformers_primary_model={"btc_usdt_4h": None},
)

cross_over_strategy.fit({"btc_usdt_4h": df}, df_triple_barrier_labels)

min_n_bars = 40

strategy = StrategyTrader(
    strategy_pipeline=cross_over_strategy,
    min_num_bars=min_n_bars,
    num_expiration_bars=number_expiration_bars,
    stop_loss_factor=stop_loss_factor,
    profit_taking_factor=profit_taking_factor
)

mizar_client.save_strategy_signal(
    strategy=strategy,
    strategy_signal_info=strategy_signal_info,
)

mizar_client.save_strategy_signal(
    strategy=strategy,
    strategy_signal_info=strategy_signal_info,
)
```

