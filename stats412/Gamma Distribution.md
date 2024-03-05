The Gamma distribution ($\text{Gamma}(r, \lambda)$) with properties $r > 0, \lambda > 0$ has pdf
$$
f(x) = \begin{cases}
\frac{\lambda^r}{\Gamma(r)}x^{r - 1}e^{-\lambda x} & x > 0 \\
0 & x \le 0
\end{cases}
$$
where $\Gamma(r)$ is the Gamma function defined as
$$
\Gamma (r) = \int_0^\infty t^{r - 1}e^{-t} dt
$$
which is well defined for $r > 0$. It is true that
- $\Gamma(r + 1) = r\Gamma(r)$ for any $r > 0$
- For $r$ integer, $\Gamma(r) = (r - 1)!$
- $\Gamma(1/2) = \sqrt \pi$
The mean and variance are
$$
\mu = \dfrac{r}{\lambda} \quad\text{and}\quad\sigma^2 = \dfrac{r}{\lambda^2}
$$
## Special Cases
- Exponential distribution: $r = 1$
- Erlang distribution: $r$ is a positive integer
- Chi-square distribution: $r = k/2, \lambda = 1/2$ where $k$ is a positive integer, referred to as the *degrees of freedom* of the distribution.