The *probability mass function* of a discrete random variable $X$ is the function
$$
p_X(x) = P(X = x) \text{ for } x \in R(X)
$$
where $R(X)$ is the range of values for $X$.

The *cumulative distribution function* (cdf) $F(x)$ is the probability that $X$ takes a value less than or equal to $x$:
$$
F(x) = P(X \le x)
$$
The cumulative distribution function is defined for all values of $x$, whereas the probability mass function is defined for only valid values of $X$.
- $F(x)$ is non-decreasing
- $F(\infty) = 1, F(-\infty) = 0$
- $F(x)$ is a stepped function
The pmf and cdf are informationally equivalent.

# Expectation
The **mean, expected value, or expectation** of a discrete random variable $X$ is
$$
E(X) = \mu_X = \sum_{x \in R(X)}xP(X = x)
$$
The **variance** of a random variable $X$ is defined as
$$
\text{Var}(X) = \sigma_X^2 = E\left[(X - \mu_X)^2\right] = \sum_{x \in R(X)} (x - \mu_X)^2 P(X = x)
$$
Equivalently:
$$
\sigma_X^2 = E(X^2) - \mu_X^2 = \sum_{x \in R(X)} x^2P(X = x) - \mu_X^2
$$
The **standard deviation** is the positive square root of the variance.

# Continuous Random Variables
Some properties of random variables need to be redefined or changed to alternate forms to better fit the properties of continuous variables.
## Probability Density
A function $f_X$ is said to be the **probability density function** or simply **density** of a continuous random variable $X$ if
$$
P(X \in B) = \int_B f_X(u)\ \text du
$$
For example:
- $P(a < X < b) = \int_a^b f(x)\ \text dx$
- $P(X = a) = \int_a^a f(x)\ \text dx = 0$
The above bullet point is different from distributions of discrete random variables.

The properties of a pdf $f(x)$:
- $f(x) \ge 0$
- $\int_{-\infty}^{\infty} f(x) = 1$
- $f(x)$ is a derivative, and therefore it is not always true that $f(x) < 1$

### Uniform Density Function
The pdf for a uniformly distributed random variable is
$$
f(x) = \begin{cases}
\dfrac{1}{b - a} & \text{if $a < x < b$} \\
0 & \text{otherwise}
\end{cases}
$$
You can denote a variable as having a certain distribution by the $\sim$ operator. For example, $X \sim \text{Uniform}(0, 1)$ denotes that $X$ is uniformly distributed over the range $(0, 1)$

### Exponential Density Function
The pdf for an exponential distribution is
$$
f(x) = \begin{cases}
\lambda e^{-\lambda x} &\text{if } x \in (0, \infty) \\
0 &\text{otherwise}
\end{cases}
$$
where $\lambda > 0$ is a parameter. If $X$ has this distribution, we denote it as $X \sim \text{Exp}(\lambda)$. The cdf of this function is
$$
F(x) = \begin{cases}
0 &x \le 0 \\
1 - e^{-\lambda x} & x > 0
\end{cases}
$$
## Redefinition of cdf
Since the pdf is a derivative, we can compute the cdf $F(x)$ as
$$
F(x) = \int_{-\infty}^x f(u)\text du \text{ for all } x
$$
where $f$ is the pdf of the random variable.

The cdf of a continuous distribution can be calculated in the same way as introduced before. It also shares the same properties with the cdf of the discrete distribution, with the one exception that the cdf is now continuous.

As with discrete random variables:
$$
P(a < X < b) = F(b) - F(a)
$$
The median of a continuous random variable is $x$ where $F(x) = 0.5$. Generally, the percentile of a distribution is the point at which the cdf equals that percent value. For example, the 90th percentile is $x$ where $F(x) = 0.9$.
## Expectation and Variance
For a continuous random variable with pdf $f_X(x)$,
- The expected value of $X$ is
$$
\mu_X = E(X) = \int_{-\infty}^\infty xf_X(x) \text dx
$$
- The variance of $X$ is 
$$
\sigma_X^2 = E\left[(X - \mu_X)^2\right] = \int_{-\infty}^\infty(x - \mu_X)^2 f_X(x)\ \text dx
$$
	or

$$
\sigma_X^2 = E(X^2) - \mu_X^2 = \int_{-\infty}^\infty x^2 f_X(x)\ \text dx - \mu_X^2
$$
## Properties of an Exponential Distribution
The mean of an exponential distribution with parameter $\lambda$ is $\dfrac{1}{\lambda}$. The variance is $\dfrac{1}{\lambda^2}$.  Deriving these uses integration by parts.