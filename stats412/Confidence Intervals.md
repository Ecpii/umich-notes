# Summary

| Population         | $\sigma$ | $n$  | $100(1 - \alpha)\%$ CI for $\mu$                         |
| ------------------ | -------- | ---- | -------------------------------------------------------- |
| $N(\mu, \sigma^2)$ | Known    | Any  | $\overline X_n \pm z_{\alpha/2} \frac{\sigma}{\sqrt 2}$  |
| $N(\mu, \sigma^2)$ | Unknown  | Any  | $\overline X_n \pm t_{n -1, \alpha/2} \frac{s}{\sqrt n}$ |
| Any                | Known    | >~30 | $\overline X_n \pm z_{\alpha/2} \frac{\sigma}{\sqrt n}$  |
| Any<br>            | Unknown  | >~30 | $\overline X_n \pm z_{\alpha/2} \frac{s}{\sqrt n}$       |
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
If $n$ is large when sampling for a proportion, then
$$
\frac{\hat p - p}{\sqrt{p(1 - p)/n}} \sim \text N(0,1)
$$
We use that value as a pivot, and therefore
$$
\hat p \pm z_{\alpha / 2}\sqrt{\hat p(1 - \hat p)/n}
$$
is a large-sample $100(1 - \alpha)\%$ confidence interval for $p$. For example, if trying to find a $95\%$ confidence interval, we would take $\alpha = 0.05$, and find $z_{0.025} = -1.96$.
The radius of the confidence interval here is often referred to as the *margin of error*. The most conservative margin of error is found at $p = 0.5$ - this would give a confidence interval of
$$
p \pm z_{\alpha / 2}\sqrt{\frac{0.5(1 - 0.5)}{n}} = p \pm \frac{z_{\alpha/2}}{2\sqrt n}
$$
The confidence interval we have talked about works well if $np > 5$ and $n(1 - p) > 5$ - we don't know the true value of $p$ but we can check these conditions with $\hat p$.

## Agresti-Coull Interval
An improved interval for small $n$ is:
$$
\tilde{p} \pm z_{\alpha/2} \sqrt{\tilde p (1 - \tilde p)/\tilde n}
$$
where $\tilde n = n + 4$ and $\tilde p = (\sum_{i = 1}^n X_i + 2)/\tilde n$
# Difference Between Population Means
If $X_1, \ldots, X_n$ is a random sample from $N(\mu_X, \sigma_X^2)$, and $Y_1, \ldots, Y_n$ is a random sample from $N(\mu_Y, \sigma_Y^2)$, then
$$
\overline X_n - \overline Y_n \sim N\left(\mu_X - \mu_Y, \frac{\sigma_X^2}{n_X} + \frac{\sigma_Y^2}{n_Y}\right)
$$
This is because for each independent pair of $X, Y$,
$$
X - Y \sim N(\mu_X - \mu_Y, \sigma_X + \sigma_Y),
$$
and for each sample mean, the variance gets divided by the size of the sample. The $100(1 - \alpha)$ confidence interval for the difference between means is
$$
\overline X_n - \overline Y_n \pm z_{\alpha / 2}\sqrt{\frac{\sigma^2_X}{n_X} + \frac{\sigma^2_Y}{n_Y}}
$$
## Small Sample Difference
If $\sigma_X = \sigma_Y$, then
$$
\frac{(\overline X_n - \overline Y_N) - (\mu_X - \mu_Y)}{s_p\sqrt{\frac{1}{n_X} + \frac{1}{n_Y}}} \sim t_{n_X + n_Y - 2}
$$
where
$$
s_p = \sqrt{
\frac{(n_X - 1)s_X^2 + (n_Y - 1)s_Y^2}{n_X + n_Y - 2}
}
$$
is known as the *pooled sample standard deviation*.

Therefore, the confidence interval is
$$
\overline X_n - \overline Y_n \pm t_{n_X + n_Y - 2, \alpha / 2}s_p \sqrt{\frac{1}{n_X} + \frac{1}{n_Y}}
$$
If $\sigma_X \ne \sigma_Y$, then
$$
\overline X_n - \overline Y_n \pm t_{v, \alpha/2} \sqrt{\frac{s^2_X}{n_X} + \frac{s^2_Y}{n_Y}}
$$
where
$$
v = \left\lfloor
\frac{\left(\frac{s_X^2}{n_X} + \frac{s_Y^2}{n_Y}\right)^2}
{\frac{(s_X^2/n_X)^2}{n_X - 1} + \frac{(s_Y^2/n_Y)^2}{n_Y - 1}}
\right\rfloor
$$
# Paired Data
Two data sets are paired if each observation in one set has a correspondence or connection with *exactly* one observation in the other data set. The advantage of considering the populations in a paired situation is that we eliminate some variability. For example, we might want to see the difference between pretest and posttest scores and can associate data per student.

We denote each pair as
$$
\begin{align*}
\text{first pair} &&X_{11}, X_{12} \\
\text{second pair} &&X_{21}, X_{22}\\
\end{align*}
$$
We are usually interested in the differences $D_i = X_{i1} - X_{i2}$ for each pair. Then, we can apply our confidence intervals and analysis as usual assuming the $D$ is our sample.

If $n$ is small, we let our pivot be
$$
\frac{\overline D_n - \mu}{s_D / \sqrt{n}} \sim t_{n - 1}
$$
where $\overline D$ is the sample mean and $s_D$ is the sample deviation, giving us a $100(1 - \alpha)\%$ confidence interval of
$$
\overline D \pm t_{n - 1, \alpha/2} \left(\frac{s_D}{\sqrt{n}}\right)
$$
If $n$ is large, we can replace the $t$ distribution by using $z_{\alpha/2}$ instead of $t_{n - 1, \alpha / 2}$ by CLT.
# Sampling Distribution
Sampling distributions are the probability distributions of statistics. For the sample mean over $N(\mu, \sigma^2)$, the sampling distribution is $N(\mu, \sigma^2/n)$. The standard error is the standard deviation of the sampling distribution of a statistic. For $\overline X$, the standard error is $\sigma/\sqrt n$.