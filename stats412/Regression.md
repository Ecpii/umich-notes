Take some paired data where $X$ is some *predictor* or *explanatory variable* and $Y$ the *response*.

The regression model is defined as
$$
Y = m(X) + \varepsilon
$$
where $m(x)$ is a *regression function* (also called a *mean response function*), and $\varepsilon$ (error) is a random variable with expectation zero and finite variance. A regression model is meant to show the relationship between two variables.

$Y$ is always a random variable but $X$ can be either random or nonrandom.

# Linear
If $m(x)$ is linear,
$$
m(x) = \beta_0 + \beta_1 x
$$
where $\beta_0$ is the intercept and $\beta_1$ is the slope. Specifically, each point is modeled by
$$
y_i = \beta_0 + \beta_1 x_i + \varepsilon_i
$$
The lack of fit is defined by
$$
S(b_0, b_1) = \sum_{i = 1}^n \Big(y_i - (b_0 + b_1x_i)\Big)^2
$$
The least squares estimates of $\beta_0, \beta_1$ are obtained by finding $b_0, b_1$ that minimize $S$. This is
$$
\hat \beta_1 = \dfrac{\sum_{i = 1}^n (x_i - \overline x)(y_i - \overline y)}{\sum_{i = 1}^n (x_i - \overline x)^2}
\quad\text{and}\quad
\hat \beta_0 = \overline y - \overline x \hat \beta_1
$$
In terms of the sample correlation coefficient $r$, sample covariance $s_{xy}$, and variance $s_y, s_x$:
$$
\hat \beta_1 = r\dfrac{s_y}{s_x}
\quad\text{and}\quad
\hat \beta_0 = \overline y - \overline x \hat \beta_1
$$
If we use these parameters, we have
$$
\hat m(x) = \hat \beta_0 + \hat \beta_1 x
$$
which is referred to as the least squares lines. Each individual $\hat y_i = \hat \beta_0 + \hat \beta_1 x$ is referred to as the *predicted value* or *fitted value* of $y_i$. The following is called the *residual*:
$$
\begin{align*}
e_i &= y - \hat y_i \\
&= (\beta_0 - \hat \beta_0) + (\beta_1 + \hat \beta_1) x_i + \varepsilon_i
\end{align*}
$$
## Correlation Coefficient
The correlation coefficient mentioned before is defined as
$$
r = \frac{s_{xy}}{s_xs_y} = \dfrac{\sum_{i = 1}^n (x_i - \overline x)(y_i - \overline y)}{\sqrt{\sum_{i = 1}^n (x_i - \overline x)^2}\sqrt{\sum_{i = 1}^n (y_i - \overline y)^2}}
$$
This always has the following properties:
- $-1 \le r \le 1$, where $r = \pm 1$ if and only if all the points lie on a straight line
- If $r > 0$, then $x_i$ and $y_i$ are positively associated (i.e. large $x_i$ go to large $y_i$ and similarly for small values)
- If $r < 0$, then $x_i$ and $y_i$ are negatively associated (i.e. large $x_i$ go to small $y_i$ and similarly for small $x_i$ with large $y_i$ values)
- If $r \approx 0$, then $x_i$ and $y_i$ are not associated in any way, or there is a non-linear relationship.
# Coefficient Of Determination
The coefficient of determination ($R^2$) is often used to assess whether a linear regression model makes sense with relation to a scatter plot.
$$
R^2 = 1 - \frac{\sum_{i = 1}^n (y_i - \hat y_i)^2}{\sum_{i = 1}^n (y_i - \overline y)^2}
$$
where $\hat y_i = \hat \beta_0 + \beta_1 x_i$ is the predicted value of $y_i$.

If
- $SST$ is the total sum of squares,
$$
\sum_{i = 1}^n (y_i - \overline y)^2
$$
- $SSE$ is the error sum of squares, and
$$
\sum_{i = 1}^n (y_i - \hat y_i)^2
$$
- $SSR$ is the regression sum of squares,
$$
\sum_{i = 1}^n (\hat y_i - \overline y)^2
$$
then
$$
SST = SSE + SSR
$$
and
$$
R^2 = \frac{SST - SSE}{SST} = \frac{SSR}{SST}
$$
