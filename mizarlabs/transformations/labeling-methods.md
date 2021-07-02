---
description: Building better targets for your model.
---

# Labeling Methods

In supervised learning, every model requires target labels, without target labels it is not possible to fit a machine learning model with features, as the model does not know what the outcomes should be. In financial machine learning, the target labels can be constructed in various ways.

**Fixed Time Horizon Method**

The most common way to construct target labels for a trading strategy is to use fixed time horizons, for example, we take the price $$p_t$$at time $$t$$and look ahead with a fixed horizon$$k$$at price $$p_{t+k}.$$ To calculate the target label we take the difference between the two prices, if the difference is positive, then we label this sample with 1 and otherwise -1. Note how this method does not take into account the intermediate prices, i.e. the target ignores the path taken from $$p_t$$to $$p_{t+k}$$, while in practice if you went long and the price dropped or increased significantly in this period, then you would have either have hit your stop-loss or profit-taking levels respectively.

**Triple Barrier Labeling Method**

The triple barrier labeling method by Prado \(2018\) takes into account the path taken when a position is taken at time $$t.$$First, we determine what our volatility-adjusted stop-loss and profit-taking levels are, these are the so-called horizontal barriers. We also define after how many periods the position should be closed out, as it is unrealistic to hold the position indefinitely, which we call the vertical barrier.

The triple barrier labeling method determines which of the horizontal and vertical barriers are hit first. In the context of taking a long position, the labels are assigned as follows. If the profit-taking level is hit first, then the label is 1. If the stop loss level is hit, then we label it with -1. If the price moves between the two barriers and hits the vertical barrier then we can either label it with 0 or we determine whether at that point in time whether we have made a loss or a profit and label it -1 or 1 respectively.

This method of creating labels is more in tune with what would actually happen in the real world and is therefore preferred over the fixed time horizon method.

**Trend Scanning Method**

The barrier levels in the triple barrier labeling are set by the user at their own discretion. The trend scanning method by Prado \(2020\) determines labels without having to set such barriers. The goal of trend scanning is to determine the dominant trend for a certain period and assign that period a label $$y_t \in \{-1, 0, 1 \},$$which corresponds with a down-trend, no-trend, or up-trend respectively. Consider a time series of prices $$\{p_t\}_{t=1,...,T}$$, to determine the label of $$p_t$$we look ahead $$L$$periods and we compute the following

$$
p_{t+l} = \beta_{0} + \beta_{1} l + \epsilon_{t+l} \\
\hat{t}_{\beta_1} = \dfrac{\hat{\beta}_1}{\hat{\sigma}_{\beta_1}}
$$

where $$l=0, ..., L - 1, L$$by taking different values for $$L$$we get different t-values. The label that is assigned to $$p_t$$ is determined by the $$L$$ for which the absolute value of the t-value $$\big|\hat{t_{\beta_1}}\big|$$is maximised.

**References**

* De Prado, M. L. \(2018\). Advances in financial machine learning. John Wiley & Sons.
* López de Prado, Marcos M. 2020. Machine Learning for Asset Managers. Elements in Quantitative Finance. Cambridge: Cambridge University Press. doi:10.1017/9781108883658.

