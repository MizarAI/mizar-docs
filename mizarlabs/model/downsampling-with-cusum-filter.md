---
description: Filtering out the noise and keeping only the informative parts of your data.
---

# Downsampling with CUSUM Filter

Typically financial time series suffer from a low signal-to-noise ratio. When the entire financial dataset is used the model will focus too much on noisy samples and not enough on highly informative samples. A way to improve the signal-to-noise ratio is to downsample the dataset, but randomly downsampling is not effective as the ratio of noisy to informative sample will persist. Instead one could apply a CUSUM filter which only creates a sample when the next values deviate sufficiently from the previous value.

Consider a locally stationary process generating IID observations $$\{y_t\}_{t=1,..,T}$$. The cumulative sums can then be defined as 

$$
S_t = \max(0, S_{t-1} +y_t - E_{t-1}[y_t])
$$

with boundary condition $$S_{0} = 0.$$ A sample is only created when $$S_{t} \ge h,$$ for some threshold $$h.$$This can be further extended to a symmetric CUSUM filter to include run-ups and run-downs such that

$$
S^+_t = \max(0, S^+_{t-1} + y_t - E_{t-1}[y_t]), S^+_0 = 0 \\
S^-_t = \min(0, S^-_{t-1} + y_t - E_{t-1}[y_t]), S^-_0 = 0 \\
S_t = \max(S^+_t, -S^-_t)
$$



