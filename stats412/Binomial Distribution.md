A binomial distribution is constructed by taking $n$ independent and identical binary trials with outcomes of 0 or 1, and counting the number of 1's in those trials. The probability of any outcome being 1 is parameterized by $p$; let $q = 1 - p$.

The random variable $X$ that holds the number of 1's in the $n$ trials has pmf
$$
p_X(x) = \begin{cases}
\binom{n}{x}p^x(1 - p)^{n - x} & x = 0, 1, \cdots, n \\
0 & \text{otherwise}
\end{cases}
$$
As with uniform distributions, we designate a random variable having this distribution by $X \sim \text{Bin}(n, p)$
## Derivation
We can derive the mean and variance of $X$ using the Bernoulli trials that compose $X$. Since we have $n$ iid variables, the expected value and variance of $X$ are
$$
E(X) = n\mu
$$
$$
\text{Var}(X) = n\sigma^2
$$
The pmf of each trial is
$$
p(x) = \begin{cases}
1 - p & x = 0 \\
p & x = 1
\end{cases}
$$
Then,
- $E(X) = p$
- $E(X^2) = p$
- $\text{Var}(X) = E(X^2) - E(X)^2 = p(1 - p)$
Then, the mean and variance of the binomial distribution are
$$
E(X) = np
$$
$$
\text{Var}(X) = np(1 - p)
$$
## Independence
if $X \sim \text{Bin}(m, p)$ and $Y \sim \text{Bin}(n, p)$ are independent, then
$$
X + Y \sim \text{Bin}(m + n, p)
$$
only if $p$ in both distributions are the same.
# Negative Binomial Distribution
The negative binomial distribution is also constructed of an amount of independent and identical Bernoulli trials. However, the value of the random variable $X$ is the number of trials needed to get $r$ successes. The pmf of $X$ is
$$
p(x) \begin{cases}
\dbinom{x - 1}{r - 1}p^r(1 - p)^{x - r} & x = r , r + 1, r + 2\ldots \\
0 & \text{otherwise}
\end{cases}
$$
This is denoted as $\text{NB}(r, p)$, and the case where $r = 1$ this is referred to as the geometric series.
## Intuition
The formula can be broken up into:
- $p^r$ - probability of getting 1 $r$ times,
- $(1 - p)^{x - r}$ - probability of getting 0 $x - r$ times
- $\dbinom{x - 1}{r - 1}$ - number of ways to arrange the $r - 1$ 1's in the first $x - 1$ elements (the last element has to be a 1 by definition)
## Expected Value and Variance
The expected value of $NB$ is
$$
E(X) = \dfrac{r}{p}
$$
and the variance is
$$
\text{Var}(X) = \dfrac{r(1 - p)}{p^2}
$$

