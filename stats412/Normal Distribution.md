A random variable $X$ with pdf
$$
f_X(x) = \frac{1}{\sqrt{2\pi}\sigma} e^{-\frac{(x - \mu)^2}{2\sigma^2}}
$$
for all $x$ is said to be normally distributed with parameters $\mu$ and $\sigma > 0$. This is also called the Gaussian Distribution.
The normal distribution is symmetric with $\mu$ as the center point.
- $E(X) = \mu$
- $\text{Var}(X) = \sigma$
## Standard Normal
If $\mu = 0, \sigma = 1$, the normal distribution is called *standard normal* and is usually denoted by $Z, z$ rather than $X, x$.
- $E(Z) = 1$
- $\text{Var}(Z) = 1$

The cdf of the standard normal distribution is
$$
\Phi(z) = \int_{-\infty}^z \frac{1}{\sqrt{2\pi}}e^{-x^2/2}dx
$$
This has no closed form formula, so usually this is tabulated or calculated using technology.

## Normal Transformations
If $X \sim N(\mu, \sigma^2)$, then
$$
E(aX + b) = a\mu + b \quad\text{and}\quad
\text{Var}(aX + b) = a^2\sigma^2
$$
If $a = \frac{1}{\sigma}$ and $b= -\frac{\mu}{\sigma}$, then this transforms $X$ to a standard normal variable - this is called **standardization**.

After standardization, we can use the table for the standard normal distribution to find probabilities:
$$
P(a \le X \le b) = \Phi\left(\frac{b - \mu}{\sigma}\right) - \Phi\left(\frac{a - \mu}{\sigma}\right)
$$
The fractions $\dfrac{b - \mu}{\sigma}$ and $\dfrac{a - \mu}{\sigma}$ are called *z-scores*. The *z-score* can refer to the number of standard deviations a number is away from the mean.

If we have a collection of $n$ independent and identically normally distributed variables, then the sample mean is
$$
\overline X \sim N(\mu, \frac{\sigma}{n})
$$
# Central Limit Theorem
If $X_0, X_1, \ldots, X_n$ are iid random variables with mean $\mu$ and variance $\sigma^2$, then let
$$
Z_n = \frac{\sqrt n (\overline X_n - \mu)}{\sigma}
$$
For large $n$, $Z_n$ approximates the standard normal distribution. The CLT works well when
- the population distribution is symmetric
- the population variance is small
- the sample size is large

## Binomial Approximation
When approximating the binomial distribution with the CLT, we find that the distribution
$$
\dfrac{X - np}{\sqrt{np(1 - p)}} \sim N(0, 1)
$$
Continuity corrections can improve the approximation - subtract $0.5$ from the left endpoint and add $0.5$ to the right endpoint.
The normal approximation works well enough as long as $np, np(1 - p) > 5$.
## Poisson Approximation
If $X \sim \text{Poisson}(\lambda)$, then when $\lambda$ is large,
$$
\dfrac{X - \lambda}{\sqrt \lambda} \sim N(0, 1)
$$
We like to use this when $\lambda > 10$.
