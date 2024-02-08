# Greatest Common Divisor
Let $x,y \in \mathbb{N}$ - The **greatest common divisor ($\text{gcd}$)** of $x$ and $y$ is is the largest $z \in \mathbb{N}$ that divides both x and y.
- if $\text{gcd}(x,y) = 1$ then x and y are **coprime**
## Naïve algorithm
With $y > x$, for $z = y..1$ return the first $z$ that divides both $x$ and $y$.
- runtime of $O(y)$
- runtime is exponential in the size of the input y, since in terms of operations the size is the log of the number - the digits or bits that the number takes up.

## Recursive Strategy
Suppose $x \ge y$, then $\text{gcd}(x, y) = \text{gcd}(y, x - y)$ 
> If $d \mid x$, then $x = nd$ for some $n \in \mathbb{Z}$. Likewise, if $d \mid y$, then $y = md$ for some $m \in \mathbb Z$. Thus, $x - y = nd - md  = (n - m)d \implies d \mid x - y$

This is used to make the **Euclidean Algorithm** to compute the greatest common divisor of two integers.
Assuming $x \ge y > 0$:
$$
\text{Euclid}(x, y) =
\begin{cases}
y & x \mathrel{\text{mod}} y = 0 \\
\text{Euclid}(y, x \mathrel{\text{mod}} y) & x \mathrel{\text{mod}} y \ne 0
\end{cases}
$$

# Potential Function Argument
The intuition behind this is
> If you start with a finite amount of water in a *leaky* bucket, then *eventually* water stops leaking out

To actually apply this, there are three things to be considered:
- what is time? (iterations, recursions)
- how is your bucket leaking - is the quantity decreasing at every time tick?
- 