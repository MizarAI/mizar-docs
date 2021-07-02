# Sample Weights

In financial time series, the samples in the training set do not contain equal amounts of information, ideally the model would focus on significant events. For example, samples wherein the subsequent period a large absolute return can be realised, are more interesting for the model than periods where small returns are made. In addition, it makes intuitive sense that recent information is more valuable than dated information in financial markets. It therefore desirable for the model to place more emphasis on recent information than dated information.

These two concepts can be formalised by calculating sample weights for each sample. These weights are then used by the model to place more emphasis on samples with a high weight. 

**Return Attribution**

To calculate the sample weight based on the sample's return, we transform the prices to log prices such that the sum of log prices is approximately equal to the return over that period. The weight for sample$$i$$with a lifespan between $$[t_{i,1}, t_{i,2}]$$ can be calculated as follows

$$
\widetilde{w}_i = \bigg|\sum_{t=t_{i,0}}^{t_{i,1}}\dfrac{r_{t-1, t}}{c_t}\bigg| \\
w_i = \dfrac{\widetilde{w}_i}{\sum_{j=1}^{I}\widetilde{w}_j}
$$

where $$c_t$$is the number of concurrent events, i.e. the number of samples that \(partially\) overlap in the period $$[t-1, t]$$. The weights are then normalised such that they sum one.

**Time Decay**

It is possible to assign more weight to recent samples than older samples by calculating time decay factor $$d \ge 0.$$To calculate these time decay factors, we use the array with the average uniqueness $$\bar{u}_i,$$where the most recent sample always receives a weight of 1. The user can control the amount of time decay with parameter $$c \in (-1, 1].$$The weight of the oldest sample is $$c,$$ for $$c\in[0,1].$$ When $$c \in (-1, 0),$$the decay factor is 0 for some samples, which implies the model will fully ignore these samples. For other samples, the decay factor can be computed with a linear piecewise function defined as

$$
d=\max(0, a + b x) \\ a=1-b\sum_{i=1}^{I}\bar{u}_i \\b = \dfrac{1-c}{\sum_{i=1}^{I}\bar{u}_i}, \forall c \in [0, 1] \\ b =\bigg[(c+1)\sum_{i=1}^{I}\bar{u}_i\bigg]^{-1}, \forall c \in (-1, 0)
$$





