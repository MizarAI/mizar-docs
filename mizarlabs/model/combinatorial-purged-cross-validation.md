# Combinatorial Purged Cross Validation

In machine learning, cross-validation is applied to assess how well models generalise over unseen data. This is achieved by splitting the training dataset into parts, a train part which is used to train the model, and a validation part which is used to assess the model on unseen data.

Machine learning models built on time series data typically suffer from overfitting, which makes cross-validation an important technique to apply to estimate the degree of overfitting, i.e. the difference between the model's performance on seen data versus unseen data.

In non-time-series settings, k-fold cross-validation is one of the most popular cross-validation schemes, however it assumes that data is drawn from an independent and identically distributed stochastic process. This assumption is violated when modeling with time-series data, as time series exhibit serial correlation. When k-fold cross-validation is used on time series, it will lead to information leakage between the folds. In particular, it is possible that information from the training set leaks into the validation set. This leads to an overestimation of the model's performance on unseen data, as it is not actually unseen data anymore due to the leakage.

To alleviate this issue with k-fold cross-validation, a more robust cross-validation scheme is developed by Prado \(2018\). Combinatorial Purged Cross Validation is similar to k-fold, but takes into account that information can leak from the train set into the validation set. The information leakage can be stopped by purging and embargoing \(removing samples in the dataset\) in the train set that is close to the validation set. This will result in better estimates of the model's performance on unseen data.

**References**

* De Prado, M. L. \(2018\). Advances in financial machine learning. John Wiley & Sons.

