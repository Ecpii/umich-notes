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
This is denoted as $\text{NB}(r, p)$, and the case where $r = 1$ this is referred to as the geometric distribution.
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
# Hypergeometric Distribution
A box contains $N$ balls, of which $R$ are red. We sample $n$ balls without replacement and let $X$ be the number of red balls.
$$
P(X = x) = \begin{cases}
\dfrac{\binom{R}{x}\binom{N-R}{n-x}}{\binom{N}{n}} & \text{max}(0, R+ n - N) \le x \le \text{min}(n, R) \\
0 &\text{otherwise}
\end{cases}
$$
If $X \sim H(N, R, n)$, then
$$
E(X) = n\dfrac{R}{N}
$$
$$
\text{Var}(X) = n\dfrac{R}{N}\left(1 - \dfrac{R}{N}\right)\dfrac{N-n}{N-1}
$$
If we let $p = \dfrac{R}{N}$,
$$
E(X) = np
$$
$$
\text{Var}(X) = np\left(1 - p\right)\dfrac{N-n}{N-1}
$$
# Poisson Distribution
The Poisson distribution is discrete with the pmf
$$
p_X(x) = e^{-\lambda} \dfrac{\lambda^x}{x!}, x = 0, 1, 2, \cdots
$$
where $\lambda > 0$ is a parameter. The mean and variance of $X$ are both equal to $\lambda$. Usually, $\lambda$ is a rate.
The binomial distribution can be well approximated by Poisson if you take $\lambda = np$. The approximation becomes exact as $n \to \infty$.

If $X \sim \text{Bin}(n,p)$ and $Y \sim \text{Poisson}(\lambda = np)$, then
$$
|P(X = x) - P(Y = y)| \le p(1 - e^{-np})
$$
The sum of two Poisson distributions is also a Poisson distribution. If $X \sim \text{Poisson}(\lambda_1)$ and $Y \sim \text{Poisson}(\lambda_2)$ are independent, then
$$
X + Y \sim \text{Poisson}(\lambda_1 + \lambda_2)
$$
# Multinomial Distribution
This distribution is similar to the binomial distribution, except now each of those $n$ trials can have $k$ outcomes. If $j = 1, \ldots, k$ and $X_j$ is the number of trials that result in outcome $j$, then the joint pmf of $X_1, \ldots, X_k$ is
$$
P(X_1 = x_1, \ldots X_k = x_k) = \begin{cases}
\dfrac{n!}{x_1!x_2!\cdots x_k!} p_1^{x_1}p_2^{x_2}\cdots p_k^{x_k} & x_I \ge 0, \sum_j x_j = n \\
0 & \text{otherwise}
\end{cases}
$$