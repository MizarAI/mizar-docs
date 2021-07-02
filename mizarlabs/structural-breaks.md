# Structural Breaks

Structural breaks in time series occur when the underlying dynamics driving the stochastic process change significantly. For example, COVID-19 has had a significant impact on the financial markets causing big changes in ways of working, travel, shopping, et cetera. The pandemic has disrupted markets, such as oil significantly, as people were traveling much less due to restrictions. Such an event can be classified as a black swan event, where the underlying dynamics which drive the time-series changes so drastically, that it invalidates some or all history up until the event. When trading strategies are unable to detect such shifts in dynamics, it can lead to severe errors and ultimately heavy losses. It is therefore beneficial to use statistical tests to automatically detect structural breaks to preempt such events and act accordingly.

Structural break tests broadly consist of two categories:

* CUSUM Tests: Checks whether the cumulative forecasting errors deviate significantly from white noise.
* Explosiveness Tests: In addition to testing deviation of the errors from white noise, it also tests for exponential growth and collapse.

**CUSUM Tests**

The Chu-Stinchcombe-White CUSUM test on levels was developed by Homm and Breitung \(2012\) ****to test departures from the log price $$y_t$$relative to the log price $$y_{n}$$where $$n>t$$.

$$
S_{n, t} = (y_t - y_n) (\hat{\sigma_t}\sqrt{t-n})^{-1} \sim \mathcal{N}(0,1) \\
\hat{\sigma_t}^2 = (t - 1)^{-1} \sum_{i=2}^{t}(\Delta y_i)^2
$$

The test statistic $$S_{n,t}$$can be compared against the time dependent critical value $$c_\alpha[n,t]$$for a one sided test to test for significance

$$
c_\alpha[n, t] = \sqrt{b_\alpha + \log(t -n)}
$$

To prevent choosing the reference level $$y_n$$arbitrarily, we calculate the test static over all $$n\in[1, t]$$and take the supremum such that $$S_t = \sup_{n \in [1, t]} \{S_{n,t}\}$$

**Explosiveness Tests**

The Chow-Type Dickey-Fuller \(SDFC\) test was developed by Gregory Chow \(1960\). Consider an autoregressive process

$$
y_t = \rho y_{t-1} + \epsilon_t
$$

where $$\epsilon_t$$is white noise. Under the null hypothesis $$y_t$$follows a random walk, i.e. $$\rho=1$$, while under the alternative hypothesis $$y_t$$starts off as a random walk, but after time $$\tau^* T$$, where $$\tau^*\in (0, 1)$$the process changes into an explosive process.

$$
H_0: \rho =1\\
H_1: y_t = \begin{cases} 
& y_{t-1} +\epsilon_t,  t=1, ... , \tau^* T \\
 & \rho y_{t-1} + \epsilon_t, t = \tau^* T, ... , T, \rho > 1
\end{cases}
$$

To calculate the test statistic, we fit the following specification with ordinary least squares

$$
\Delta y_t = \delta y_{t-1} D_t[\tau^*] + \epsilon_t
$$

 where the dummy variable $$D_t[\tau^*]$$is 0 when $$t < \tau^*T$$and 1 when $$t\ge\tau^*T$$, under the null hypothesis $$H_0: \delta = 0$$and under the alternative hypothesis $$H_1: \delta > 1$$, we define the following test statistic 

$$
DFC_{\tau^*} = \dfrac{\hat{\delta}}{\hat{\sigma}_{\delta}}
$$

In practice $$\tau^*$$is not known, we therefore try all possible $$\tau^*$$and take the maximum such that



$$
SDFC = \sup_{\tau^*\in[\tau_0, 1-\tau_0]} \{ DFC_{\tau^*}\}
$$

where we take $$\tau_0$$sufficiently large, such that the specification always has sufficient data to fit with at the start and the end. The main drawback of this test is that a single bubble is assumed, while in reality there can be multiple.

The Supremum Augment Dickey-Fuller \(SADF\) test by Phillips, Wu and Yu \(2011\) tests for periodically collapsing bubble with the following specification

$$
\Delta y_t = \alpha + \beta y_{t-1} + \sum_{l=1}^L \gamma_l \Delta y_{t-l} + \epsilon_t
$$

where we test under the null hypothesis $$H_0: \beta \leq 0$$and under the alternative hypothesis $$H_1: \beta > 0.$$For each point $$t_0 \in [1, t - \tau]$$the above mentioned specification is fitted with backwards expanding start points and for each point we calculate $$ADF_{t_0, t} = \dfrac{\hat{\beta}_{t_0, t}}{\hat{\sigma_{\beta_{t_0, t}}}}$$, we then define

$$
SADF_t = \sup_{t_0 \in [1, t - \tau]}\{ ADF_{t_0, t}\}
$$

where $$\tau$$is taken sufficiently large to ensure the specification at the end can be fitted with sufficient data.

**References**

* Ulrich Homm, Jörg Breitung, Testing for Speculative Bubbles in Stock Markets: A Comparison of Alternative Methods, _Journal of Financial Econometrics_, Volume 10, Issue 1, Winter 2012, Pages 198–231, [https://doi.org/10.1093/jjfinec/nbr009](https://doi.org/10.1093/jjfinec/nbr009)
* Chow, Gregory C. "Tests of Equality Between Sets of Coefficients in Two Linear Regressions." Econometrica 28, no. 3 \(1960\): 591-605. Accessed March 15, 2021. doi:10.2307/1910133.
* Phillips, Peter CB, Yangru Wu, and Jun Yu. "Explosive behavior in the 1990s Nasdaq: When did exuberance escalate asset values?." International economic review 52, no. 1 \(2011\): 201-226.

