# Summary

| Population         | $\sigma$ | $n$  | $100(1 - \alpha)\%$ CI for $\mu$                         |
| ------------------ | -------- | ---- | -------------------------------------------------------- |
| $N(\mu, \sigma^2)$ | Known    | Any  | $\overline X_n \pm z_{\alpha/2} \frac{\sigma}{\sqrt 2}$  |
| $N(\mu, \sigma^2)$ | Unknown  | Any  | $\overline X_n \pm t_{n -1, \alpha/2} \frac{s}{\sqrt n}$ |
| Any                | Known    | >~30 | $\overline X_n \pm z_{\alpha/2} \frac{\sigma}{\sqrt 2}$  |
| Any<br>            | Unknown  | >~30 | $\overline X_n \pm z_{\alpha/2} \frac{s}{\sqrt 2}$       |
A confidence interval should
- include the actual value we attempt to estimate a reasonable amount of the time,
- and be small
An example confidence interval around the normal distribution is
$$
\overline X_n \pm a\frac{\sigma}{\sqrt n}
$$
The probability $2\Phi(a) - 1$ is usually known as the *confidence level/coefficient*.

## Normal Distribution Construction
For a sample $X_0, X_1, \ldots, X_n$ taken from $N(\mu, \sigma^2)$, the $100(1 - \alpha)\%$ confidence interval is
$$
\overline X_n \pm z_{\alpha/2} \frac{\sigma}{\sqrt 2}
$$
where $z_p$ is the $1 - p$ quantile of $N(0, 1)$.
## Large Sample Confidence Intervals
When the sample size $n$ is large, then we can use the standard deviation of the sample $s$ instead of the actual value $\sigma$. Typically, this means that $n > 30$
## Small Sample
The $t$-distribution a parameterizable distribution with parameter $v$ (often denoted $t_v$) that looks similar to the normal distribution. $v$ is also known as the *degrees of freedom* of the distribution. When $v > 30$, the $t$-distribution is practically indistinguishable from the normal distribution. The $t$-distribution is slightly flatter than normal.
The pdf is
$$
f(t) = \frac{\Gamma\left(\frac{v + 1}{2}\right)}{\sqrt{v\pi}\Gamma\left(\frac{v}{2}\right)} \left(1 + \frac{t^2}{v}\right)^{-\frac{v + 1}{2}}
$$
If a sample $X_1, \ldots, X_n$ comes from $N(\mu, \sigma^2)$, then
$$
\frac{\overline X_n - \mu}{s/\sqrt{n}}
$$
has a $t$-distribution with $v = n - 1$. Then,
$$
P\left(-t_{n - 1, \alpha/2} < \frac{\overline X_n - \mu}{s/\sqrt{n}} < t_{n - 1, \alpha/2} \right) = 1 - \alpha
$$
## Proportion
$$
\hat p \pm z_{\alpha / 2}\sqrt{\hat p(1 - \hat p)/n}
$$
is a large-sample $100(1 - \alpha)\%$ confident interval for $p$.