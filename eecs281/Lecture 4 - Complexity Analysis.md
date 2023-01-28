Primitive operations:
- variable assignment
- arithmetic operation
- comparison
- array indexing or pointer reference
- function call
- function return
a function $f(n)$ is $O(g(n))$ if and only if for
$$
\exists c > 0, \exists n_0 >= 0,
$$
$$
\forall n > n_0, f(n) < cg(n)
$$
Alternatively, a sufficient but not necessary condition:
$$
\exists d \in \mathbb{R}, \lim_{n \to \infty} \dfrac{f(n)}{g(n)} = d
$$

|Big O|Big $\Theta$|Big $\Omega$|
|---|---|---|
|Upper bound|Tight bound|Lower bound|
|defined above|$(n) = \Theta (g(n)) \iff \exists n_0, c_1, c_2, \forall n \ge n_0,$<br>$c_1g(n) \le f(n) \le c_2g(n)$|$\exists n_0,c, \forall n \ge n_0,$<br>$f(n) \ge cg(n)$|

Alternatively, big $\Theta$ is equal to the intersction of Big O and Big $\Omega$.
## Amortized Complexity
- used when complexity is sometives very expensive but most times not that expensive
- Considers the average cost of an operation over a sequence of operations
$$

$$