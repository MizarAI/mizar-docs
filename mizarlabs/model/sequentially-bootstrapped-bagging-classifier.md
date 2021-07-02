# Sequentially Bootstrapped Bagging Classifier

When developing a machine learning model for a trading strategy users typically resort to classifiers to predict whether they should buy, sell or do nothing. A wide range of models are available, but typically a nonparametric model such as a random forest is preferred as financial time series typically have complicated nonlinear relationships that are unknown. A nonparametric model can discover these relationships by itself. 

Machine learning models suffer from three errors in general:

* Bias: failure to recognise important relationships between features and the target labels.
* Variance: sensitive to small changes in the training set.
* Noise: unpredictable changes in the data or measurement errors.

Ensemble methods combine a set of weak learners \(e.g. single decision tree\) in order to develop a stronger learner that performs better than the individual ones. These methods help reduce bias and/or variance.

Examples of these ensemble methods are random forest and bagging classifiers. These methods also typically bootstrap the training data, i.e. draw random samples from the training data. This is done to reduce the variance in the forecasts of the model. The bootstrap aggregation uses a uniform distribution to sample the data, but to get more diverse datasets it would be better to sample according to the average uniqueness of the samples.

The sequentially bootstrapped bagging classifier is an ensemble model, which samples according to the average uniqueness of the samples. When a sample $$i$$is added to the bootstrapped dataset, it reduces the probability of sampling neighbouring samples, as the sample$$i$$reduces the uniqueness of these samples. This bootstrapping scheme increases the likelihood that the bootstrapped dataset contains more diverse data, which helps reduce the variance in forecasts.







