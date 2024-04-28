$H_0$ is the null hypothesis, which is a statement that usually states something similar to the idea that there is no change, difference, relationship, etc.
$H_1/H_a$ is the alternative hypothesis, which states that something does happen, that we can draw a conclusion, etc.

- The null and alternative hypotheses should not be true at the same time
- The hypotheses are always statements about the population, and not the sample

The process for a hypothesis testing problem:
- Formulate $H_0$ and $H_1$
- Collect data
- Pick a test statistic and decide what test to use
- Decide whether we should reject $H_0$ in favor of $H_1$. We never accept $H_0$.

The $p$-value is the probability of getting a random sample for which the test statistic value is as extreme or more extreme (in the direction of $H_1$) than the observed value.

| $H_0$           | $H_1$           | $p$-value                      |
| --------------- | --------------- | ------------------------------ |
| $\mu \le \mu_0$ | $\mu > \mu_0$   | $1 - \Phi(z)$                  |
| $\mu \ge \mu_0$ | $\mu < \mu_0$   | $\Phi(z)$                      |
| $\mu = \mu_0$   | $\mu \ne \mu_0$ | $2(1 - \Phi(\lvert z \rvert))$ |

**Fixed-Level Testing** - Pick an $\alpha$ such that if $p$-value is less than $\alpha$, we reject $H_0$. $\alpha$ is known as the significance level of this test.

# Difference Between Means
$$
Z = \dfrac{\overline X - \overline Y - \Delta_0}{\sqrt{\frac{\sigma^2_X}{n_X} + \frac{\sigma^2_Y}{n_Y}}}
$$
If the sample sizes are not necessarily large but we assume that the population distributions are normal with unknown and unequal variances, then
$$
T = \dfrac{(\overline X - \overline Y) - \Delta_0}{\sqrt{\dfrac{s_X^2}{n_X} + \dfrac{s_Y^2}{n_Y}}} \sim t_v
$$
where 
$$
v = \left\lfloor
\frac{\left(\frac{s_X^2}{n_X} + \frac{s_Y^2}{n_Y}\right)^2}
{\frac{(s_X^2/n_X)^2}{n_X - 1} + \frac{(s_Y^2/n_Y)^2}{n_Y - 1}}
\right\rfloor
$$
Identical to [[Confidence Intervals#Small Sample Difference]]. If the population distributions are normal but with equal variances, then
$$
T = \dfrac
{(\overline X - \overline Y) - \Delta_0}
{s_P\sqrt{\frac{1}{n_X} + \frac{1}{n_Y}}} \sim t_{n_X + n_Y - 2}
$$
where
$$
s_p = \sqrt{\frac{(n_x - 1)s_X^2 + (n_Y - 1)s_Y^2}{n_X + n_Y - 2}}
$$
# Paired Data
$$
T = \dfrac{\overline D - \mu_0}{s_D/\sqrt n} \sim t_{n - 1}
$$
If the sample is large, use $z$ scores. The value $\overline D$ represents the mean of all the paired differences
$$
D_1 = X_1 - Y_1, D_2 = X_2 - Y_2, \cdots
$$
# Proportion
$$
Z = \frac
{\hat p - p_0}
{\sqrt{\frac{p_0(1 - p_0)}{n}}} \sim N(0, 1)
$$
## Differences
$$
Z = \frac{\hat p_X - \hat p_Y}
{\sqrt{\hat p(1 - \hat p)\left(\frac{1}{n_X} + \frac{1}{n_Y}\right)}}
$$
where $\hat p = \dfrac{\sum X_i + \sum y_i}{n_X + n_Y}$, and $\hat p_X, \hat p_Y$ are the sample proportions for the $X$ and $Y$ samples respectively.

# Testing Variance
To test variance with $\alpha$-level confidence, we have to calculate the sample variance:
$$
s^2 = \frac{1}{n - 1} \sum_{i = 1}^n (X_I - \overline X)^2
$$
The test statistics we will use are
$$
\chi^2 = \frac{(n - 1)s^2}{\sigma^2_0}
$$
$$
\chi_{n - 1, p}^2 = 100(1 - p)^{\text{th}}
$$
percentile of the $\chi^2$ distribution with $n - 1$ degrees of freedom. Our tests are

| $H_0$                     | $H_1$                     | Decision rule for rejecting $H_0$                                               |
| ------------------------- | ------------------------- | ------------------------------------------------------------------------------- |
| $\sigma^2 \le \sigma_0^2$ | $\sigma^2 > \sigma_0^2$   | $\chi^2 > \chi^2_{n - 1, \alpha}$                                               |
| $\sigma^2 \ge \sigma_0^2$ | $\sigma^2 < \sigma_0^2$   | $\chi^2 < \chi^2_{n - 1, 1 - \alpha}$                                           |
| $\sigma^2 = \sigma_0^2$   | $\sigma^2 \ne \sigma_0^2$ | $\chi^2 > \chi^2_{n - 1, \alpha/2}$ or $\chi^2 < \chi^2_{n - 1,  1 - \alpha/2}$ |
## Variance Equality
Let
$$
\begin{gather*}
s_1^2 = \frac{1}{m - 1} \sum_{i = 1}^m (X_i - \overline X)^2 \\
s_2^2 = \frac{1}{n - 1} \sum_{i = 1}^n (Y_i - \overline Y)^2 \\
\end{gather*}
$$

| $H_0$                                 | $H_1$                                 | Decision rule for rejecting $H_0$                                        |
| ------------------------------------- | ------------------------------------- | ------------------------------------------------------------------------ |
| $\frac{\sigma_1^2}{\sigma_2^2} \le 1$ | $\frac{\sigma_1^2}{\sigma_2^2} > 1$   | $f > F_{m - 1, n - 1, \alpha}$                                           |
| $\frac{\sigma_1^2}{\sigma_2^2} \ge 1$ | $\frac{\sigma_1^2}{\sigma_2^2} < 1$   | $f < F_{m - 1, n - 1, 1 -\alpha}$                                        |
| $\frac{\sigma_1^2}{\sigma_2^2} = 1$   | $\frac{\sigma_1^2}{\sigma_2^2} \ne 1$ | $f > F_{m - 1, n - 1, \alpha/2}$ or $f < F_{m - 1, n - 1, 1 - \alpha/2}$ |
where f is the computed value of the test statistic
$$
F = \frac{s_1^2}{s_2^2}
$$
and $F_{v_1, v_2, p}$ is the $100(1 - p)$th percentile of the $F$ distribution with $v_1, v_2$ degrees of freedom.
A property we can use for the $F$ distribution is
$$
F_{v_1, v_2, 1 - \alpha} = \frac{1}{F_{v_2, v_1, \alpha}}
$$
to find lower percentiles from upper percentiles

# Error
|             | Reject $H_0$ | Fail to reject $H_0$ |
| ----------- | ------------ | -------------------- |
| $H_0$ true  | Type I Error |                      |
| $H_0$ false |              | Type II Error        |
The set of $x_1, \ldots, x_n$ for which we reject $H_0$ is called the *critical region* or *rejection region*.

If the true value of the population mean is $\mu_t$, then the probability of a Type I error is
$$
P\left(Z > \dfrac{\mu_0 - \mu_t}{\sigma / \sqrt{n}} + z_\alpha \right)
$$
The probability of making a Type II error is
$$
P\left(Z < \dfrac{\mu_0 - \mu_t}{\sigma / \sqrt{n}} + z_\alpha \right)
$$
For small $\alpha$, the probability of Type I errors is small, but is larger for Type II errors. Similarly, for large $\alpha$, the probability of Type II errors is small, but larger for Type I errors.
The probability of a Type II error is known as $1 - \beta$, where $\beta$ is referred to as the **power** of the test.