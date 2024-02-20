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
# Continuous Random Variables
A function of two variables $f(x,y)$ is the joint pdf of $X$ and $Y$ if for every region $B \subset \mathbb{R}^2$,
$$
P((X, Y) \in B) = \int \int_{(x, y) \in B} f(x,y)dxdy
$$
The function should also satisfy
- $f(x, y) \ge 0$ and
- $\int_{\mathbb{R}^2} f(x,y) dxdy = 1$
## Uniform Distribution
For the uniform distribution, where $D$ is some continuous set in the two-dimensional plane,
$$
f_{X,Y}(x, y) = \begin{cases}
\frac{1}{\text{Area}(D)} & (x, y) \in D \\
0 &\text{elsewhere}
\end{cases}
$$
## Conditional Expectation
The conditional expectation of a distribution like this is
$$
\mu_{Y | X} = \int_{-\infty}^{\infty}y f_{Y | X} (y | X) dy
$$
## Conditional Variance
$$
\text{Var}(Y|X = x) = \int_{-\infty}^{\infty}(y - \mu_{Y|X}(x))^2 f_{Y|X}(x, y) dx
$$
# Independent Events
The joint probability of independent events is the product of each of those events:
$$
P(X_1 \in A_1 \cap X_2 \in A_2 \cap \cdots \cap X_n \in A_n)
= P(X_1 \in A_1)P(X_2 \in A_2) \cdots P(X_n \in A_n)
$$
If $X_i$ are identical independently distributed variables with a common marginal pdf $f(x)$, then their joint pdf is
$$
f_{X_1,\ldots,X_n}(x_1,\ldots,x_n) = f(x_1)\cdots f(x_n)
$$
