Recurrence Relations decribe how problems depend of subproblems.
$$
x^n = \begin{cases}
1  &n == 0\\
x * x^{n - 1} & n > 0
\end{cases}
$$
## Solving Recurrence Relations
**substitution** - you keep expanding the inner expression, find a pattern, and substitute back to the original expression.
## Table of Common Recurrence Relations
|Recurrence|Example|Complexity|
|---|---|---|
|$T(n) = T(n/2) + c$|Binary Search|$\Theta(\log n)$|
|$T(n) = T(n - 1) + c$|Linear Search|$\Theta(n)$|
|$T(n) = 2T(n/2) + c$|Tree Traversal|$\Theta(n)$|
|$T(n) = T(n - 1) + c_1 * n + c_2$|Selection/etc. Sorts|$\Theta(n^2)$|
|$T(n) = 2T(n/2) + c_1 * n + c_2$|Merge/Quick Sorts|$\Theta(n\log n)$|
# Master Theorem
If you have a recurrence relation of form
$$
T(n) = aT(\dfrac{n}{c}) + f(n) \\
$$
$$
T(1) = c_0 \quad \text{or} \quad T(0) = c_0
$$
where $a \ge 1, b > 1$, and taking $c$ to be the degree of big theta complexity of $f(n)$ (i.e. $(\Theta (n^c) = \Theta (f(n))$), the following is the time complexity of the recurrence relation.
$$
T(n) \in \begin{cases}
	\Theta(n^{\log_b a}) &\text{if } a > b^c \\
	\Theta(n^{c} \log n) &\text{if } a = b^c \\
	\Theta(n^{c}) &\text{if } a < b^c \\
\end{cases}
$$
The intuition behind the comparisons is to see which side dominates. If $a > b^c$, it's like the recursive part is contributing more than the functional term.
## When to Not Use
You cannot use the Master Theorem if
- $T(n)$ is not monotonic ($T(n) = \sin n$)
- $f(n)$ is not a polynomial ($f(n) = 2^n$)
- $b$ cannot be expressed as a constant ($T(n) = $T(\sqrt{\sin n})$)
- 