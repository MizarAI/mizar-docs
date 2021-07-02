# Bet Sizing

Building a trading strategy with a model that predicts the side of the trade can be used to open positions, but opening the position with a predetermined fixed size can be inefficient. A better way would be to size your position according to how confident the model is about the prediction. This concept is called bet sizing and the following sections will formalise this concept further.

When metalabeling is applied on top of a primary model, which predicts the side of the trade, the metalabelling model outputs a predicted probability that can be used to determine the size. The metalabeling model is a binary classifier, which predicts whether to take or not take the trade. 

The goal is to test the null hypothesis $$H_0: p[x =1] = \dfrac{1}{2}, $$where $$p[x = 1]$$is the probability whether the side is correct and $$x \in \{-1, 1\}$$, where -1 and 1 represents short and long respectively. The test statistic $$z$$is defined as

$$
z = \dfrac{p[x=1] - \dfrac{1}{2}}{\sqrt{p[x=1](1-p[x=1])}} \sim \mathcal{N}(0, 1), z \in (-\infty, \infty)
$$

when the metalabelling model predicts $$p[x=1]$$, we compute the $$z$$test statistic, which we can put into the CDF of the standard normal distribution to get a bet size. However, this can lead to excessive trading with small amounts when the predicted probability $$p[x=1]$$is close to 0.5. To filter out these noisy trades, we can discretise the CDF in steps such that probabilities close 0.5, are floored to a size of 0.

