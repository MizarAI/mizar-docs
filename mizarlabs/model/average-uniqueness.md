# Average Uniqueness

When labels for samples are created without a fixed horizon \(e.g. triple barrier labeling method\), they each span a different period. These samples can therefore overlap with other samples in various degrees. Samples that do not overlap much with other samples are more unique and are therefore more interesting for the model to look at. This becomes more relevant for machine learning models which bootstrap the training data by random sampling from the dataset, however samples are bootstrapped according to a uniform distribution. This implies that samples that overlap much with other samples are as likely to be sampled as more unique samples that do not overlap with other samples. Ideally, we would therefore like to bootstrap the samples according to their uniqueness to get a more diverse bootstrapped dataset.

**Number of Concurrent Events**

To calculate the average uniqueness, we first have to calculate the number of concurrent events. This can be calculated with an indicator matrix.

$$
1_{t, i} = \begin{bmatrix} 
1 & 1 & 0 \\ 
1 & 1 & 0 \\
0 & 1&  0 \\
0 & 1 & 1 \\
\end{bmatrix}
$$

the rows represent time periods $$t=1,...,T$$and the columns represent the samples $$i=1,...,I.$$In the above example the $$T=4$$and $$I=3.$$To calculate the number of concurrent events we sum over the columns $$c_t = \sum_{i=1}^{I}1_i$$, in this example the number of concurrent events are $$2, 2, 1, 2.$$

**Average Uniqueness**

The uniqueness for sample $$i$$ at time $$t$$can be calculated with$$u_i=\dfrac{1_{t, i}}{c_t}.$$In this example, the uniqueness matrix is

$$
\begin{bmatrix}  
0.5 & 0.5 & 0 \\ 
0.5 & 0.5 & 0 \\ 
0 & 1 & 0 \\
0 & 0.5 & 0.5 \\

\end{bmatrix}
$$

To calculate the average uniqueness we take the average of the uniqueness values over $$t$$

$$
\bar{u}_i = \dfrac{\sum_{t=1}^{T}u_{t, i}}{\sum_{t=1}^{T}1_{t,i}}.
$$

In our example, the average uniquenesses of the samples are 0.5, 0.83, and 0.5 respectively.

