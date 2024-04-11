If $X$ is a discrete random variable that can take on values in $k$ categories, and
$$
\begin{align*}
H_0&: p(i) = p_0(i) &\text{for all } i \in [k] \\
H_1&: p(i) \ne p_0(i) &\text{for all } i \in [k]
\end{align*}
$$
Then the test statistic
$$
\chi^2 = \sum_{i = 1}^k \frac{(O_i - E_i)^2}{E_i}
$$
is distributed as $\chi^2$ with $k - 1$ degrees of freedom, as long as $E_j \ge 5$ for all $j$.
The $p$-value of this test is the area to the right of the computed value of $\chi$ under the $\chi^2$ pdf with $k - 1$ degrees of freedom.

Alternatively, we reject $H_0$ if $\chi^2 >  \chi_{k - 1, \alpha}$ to test at the $\alpha$ level.
# Homogeneity
The null hypothesis in a test of homogeneity states that the distribution of a categorical response variable is the same in each population. We can generate expected values for all cases by combining results and averaging. 
The table that stores the values is called a **contigency table**
![[Pasted image 20240409113321.png]]
Then, with the expected values, our test statistic is
$$
\chi^2 = \sum_{i}^I \sum_{j}^J \frac{(O_{ij} - E_{ij})^2}{E_{ij}}
$$
which is distributed as $\chi^2$ with $(I - 1) (J - 1)$ degrees of freedom.