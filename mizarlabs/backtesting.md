# Strategy Backtesting

Assessing the performance of your trading strategy is a crucial step in the development process, this is typically done by backtesting the model on a period in the past and see how well it would have fared in those market conditions. Financial machine learning models are typically assessed by several metrics, such as the [Sharpe ratio](https://www.investopedia.com/terms/s/sharperatio.asp) and the [maximum drawdown](https://www.investopedia.com/terms/m/maximum-drawdown-mdd.asp#:~:text=A%20maximum%20drawdown%20%28MDD%29%20is,over%20a%20specified%20time%20period.).

A common pitfall with backtesting is multiple repetitions of the backtest on the same period until a satisfactory result has been achieved. Prado \(2018\) even shows that it is possible to achieve any Sharpe ratio as long as you can repeat the backtest multiple times.

To prevent the artificial inflation of the Sharpe ratio, the user should take into account how many times the backtest has been run and correct for the number of backtests. In addition, the user could also consider generating multiple paths with combinatorial purged cross-validation to prevent overfitting to a specific part in the past, please refer to Prado \(2018\) for more details on how to generate these paths.

The Mizar platform offers a backtesting service to its developers and users. When a new strategy is uploaded to the platform it is assessed on its performance in an objective manner and multiple performance metrics will be computed. Afterward, these results are consolidated in a single rating to make it easier to rank the strategies in the marketplace. Users can view the backtest results and make an informed decision on whether they want to invest in an uploaded strategy.

**References**

* De Prado, M. L. \(2018\). Advances in financial machine learning. John Wiley & Sons.



