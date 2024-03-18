
# Exponential Distribution
The pdf of an exponential distribution is
$$
f(x) = \begin{cases}
\lambda e^{-\lambda x} & x > 0 \\ 
0 & x \le 0
\end{cases}
$$
The cdf is
$$
F(X) = \begin{cases}
1 - e^{-\lambda x} & x > 0 \\
0 & x \le 0
\end{cases}
$$
The mean of an exponential distribution with parameter $\lambda$ is $\dfrac{1}{\lambda}$. The variance is $\dfrac{1}{\lambda^2}$.  Deriving these uses integration by parts. An exponential distribution also has the "memoryless" property:
For two numbers $t, s$
$$
P(X > t + s |X > s) = P(X > t)
$$
This is **only** true for the exponential distribution - it is a defining property.