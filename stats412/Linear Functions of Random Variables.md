If $X$ is a random variable,
- Adding a constant $b$ to $X$ means the entire distribution shifts by $b$. The mean, median, and quartiles change by $b$, but the standard deviation and range do not.
- Multiplying a constant $a$ to $x$ means that both positional and variational properties of the distribution change. The standard deviation is scaled by $|a|$, and the mean is scaled by $a$.

More generally, in the form $aX + b$, we have that
$$
\begin{align*}
\mu_{aX + b} &= a\mu_X + b \\
\sigma_{aX + b}^2 &= a^2\sigma_X^2 \\
\sigma_{aX + b} &= |a|\sigma_X
\end{align*}
$$
The mean of the sum of random variables is the sum of the means of the random variables, even if the random variables are multiplied by constants. If some random variables are independent, the variability of the variables sum together. Only if that condition is true.

# Independent Identically Distributed Variables
If $X_1, X_2, \ldots, X_n$ are independent random variables and all have the same distribution, we can think of the variables as a random sample chosen from some population. We say that they are **independent and identically distributed**.

The sample mean
$$
\bar X = \dfrac{X_1, X_2, \ldots, X_n}{n}
$$
is equal to the mean of the population as a whole.

The variance of the sample mean is the variance of population as a whole divided by $n$:
$$
\sigma_{\bar X}^2 = \dfrac{\sigma^2}{n}
$$
