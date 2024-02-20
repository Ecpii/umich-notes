The covariance of two random variables $X$ and $Y$ is
$$
\text{Cov}(X, Y) = E\Big[(X - \mu_X)(Y-\mu_Y)\Big]
$$
For discrete random variables, this is
$$
\text{Cov}(X, Y) = \sum_x \sum_y (x - \mu_X)(y - \mu_Y)p_{X,Y}(x, y)
$$
For continuous random variables, this is
$$
\text{Cov}(X, Y) = \int_x \int_y (x - \mu_X)(y - \mu_Y) f_{X,Y}(x, y) \text dy \text dz
$$
## Interpretation
The sign of the covariance reveals whether large/small values of $X$ go with large/small values of $Y$.
- If the covariance is positive, then large values of $X$ tend to go with large values of $Y$ and vice versa with small values.
- If the covariance is negative, then large values of $X$ tend to go with small values of $Y$ and vice versa.
The unit of the covariance is the units of $X$ multiplied by the units of $Y$, so it is not always useful to interpret the magnitude of the covariance. To remedy this, we define a unitless value called the **correlation**:
$$
\rho_{X,Y} = \dfrac{\text{Cov}(X,Y)}{\sigma_X\sigma_Y}
$$
This is always a value in $[-1, 1]$, where -1 represents a perfect negative correlation and 1 represents a perfect correlation (all the points lie on a straight line).

## Independence
If the random variables $X$ and $Y$ are independent, then the covariance and correlation are 0. The converse is not necessarily true though.
## Dependence
We can now define the variance of a sum of dependent random variables:
$$
\text{Var}(c_1X_1 + c_2X_2 + \cdots + c_nX_n) = \sum_{i = 1}^n c_i^2 \sigma_{X_i}^2 + 2\sum_{1 \le i < j \le n}c_ic_j\text{Cov}(X_i, X_j)
$$
In the case of two variables, this is
$$
\text{Var}(aX + bY) = a^2\sigma_X^2 + b^2\sigma_Y^2 + 2ab\text{Cov}(X, Y)
$$
