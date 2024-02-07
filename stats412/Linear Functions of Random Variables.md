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
# Joint Distributions of Random Variables
The joint distribution of two discrete random variables $X, Y$ is
$$
P((X, Y) \in B)
$$
where $B$ is a set of pairs of possible values for $X$ and $Y$. We can define a pmf of $X$ and $Y$ such that
$$
p_{X, Y}(x, y) = P(X = x \text{ and } Y=y)
$$
A joint pmf must satisfy
- $p(x, y) \ge 0$
- $\sum_x \sum_y p(x, y) = 1$
A pmf can be conceptualized as a table:
![[Pasted image 20240206104802.png]]
We can use the row/column sums to generate pmfs for each of the individual variables $x$ and $y$. This is an application of the **Law of Total Probability**, which states that
$$
P(A) = \sum_i^n P(A \cap B_i)
$$
where the $B$ events do not overlap and partition the entire space.

Since these pmfs appear in the margins of the table, we refer to them as marginal pmfs. In a formula: 
$$
p_Y(y) = \sum_x p_{X,Y}(x, y)
$$
The conditional pmf of $Y$ given $X = x$ is defined as
$$
p_{Y | X}(y|x) = \dfrac{p_{X,Y}(x, y)}{p_X(x)}
$$
This is a function of $Y$ on fixed $x$, and is a valid pmf; it satisfies:
- $p_{Y|X}(y|x) \ge 0$ for all $y$
- $\sum_y p_{Y|X}(y|x) = 1$
