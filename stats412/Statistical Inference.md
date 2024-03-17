Formal statistical inference starts with an assumption about the population distribution - then an attempt to identify the parameters of assumed distribution.
## Parametric Distributions
A parametric distribution is a distribution whose form is completely determined by a parameter $\theta$. The set of all possible values of $\theta$ is called the parameter space and is often labeled as $\Theta$. Determining what $\theta$ is is referred to as **parametric inference.**

# Point Estimation
If we have a random sample $X_1, X_2, \ldots X_n$ drawn from a parametric distribution with parameter $\theta$, point estimation is the process to find a variable $\hat \theta$ which is a good estimate of $\theta$.
- $\hat \theta$ is a **statistic** from the sample - it is computed explicitly from $X_1, X_2, \ldots X_n$, and is sometimes notated as $\hat \theta(X_1, X_2, \ldots X_n)$.
- In a similar vein, $\hat \theta$ is often referred to as an **estimator** and $\hat \theta(X_1, X_2, \ldots X_n)$ is referred to as the **estimate**.
To determine the quality of an estimator, we would conduct many rounds of simulations based on the model to produce samples and estimates.
## Bias
The *bias* of an estimator $\hat \theta$ is defined as
$$
\text{Bias}(\hat \theta) = E(\hat \theta) - \theta
$$
It is desirable that the bias is small for all possible $\theta$.
## Variance
The variance of the estimator is
$$
\text{Var}(\hat \theta) =  \sigma_{\hat \theta}^2 = E[\hat \theta - E(\hat \theta)]^2
$$
It is also desirable to have small values of variance.

## MSE
The **mean squared error** is defined as
$$
\text{MSE}(\hat \theta) = E(\hat \theta - \theta)^2 = \text{Bias}(\hat \theta)^2 + \text{Var}(\hat \theta)
$$
which is widely used as area. Often, the square root of this is used, which is known as the **root mean squared error**.
If $\hat \theta$ is unbiased, then
$$
\text{MSE}(\hat \theta) = \text{Var}(\hat \theta)
$$
for all $\theta$.
### Sample Mean
The sample mean is a reasonable estimator. It is unbiased and the variance is $\frac{\sigma^2}{n}$.
## Maximum Likelihood Estimation
Maximum likelihood estimation is an approach that produces good estimators for most situations, and is the most popular procedure in statistics. 
We take every possible value of the parameter, simulate the distribution with that parameter, and take the parameter values that are closest to the measured results or sample we have.

Let $X_1, \ldots, X_n$ is some random sample from some distribution with parameter $\theta$. Then, if $f(t_1, \ldots, t_n;\theta)$ is the joint pdf/pmf, the function
$$
L(\theta) = f(x_1, \ldots, x_n, \theta)
$$
is known as the likelihood function of the data. We then create an estimate by finding the maximum of this function through taking its derivative. It may also be preferrable to derive the log of the likelihood if it is easier.
$$
\ell (\theta) = \ln L(\theta)
$$
This can turn a product of functions into a sum because of log rules.
- The MLE is invariant under transformations
- For many models, the MLE is the optimal estimator in terms of MSE when the sample size is large.
- The MLE may not exist or be unique or exist in some situations.