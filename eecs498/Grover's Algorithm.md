Unstructured search problem. With an arbitrary function and a database of items, find which input satisfies a function.

Grover starts by making a superposition of inputs into an oracle. Interference is used to map global properties to orthogonal states. Then, it rotates the state to map the properties to the measurable poles.

Consider a phase flip oracle $U_\omega$ with target qubit $\ket -$. Then,
$$
U_\omega\ket x = \begin{cases}
\ket x &x \ne \omega \\
-\ket x & x = \omega
\end{cases}
$$
Grover's algorithm uses **amplitude amplification**, which means that there is a process that can increase the probability of a correct answer being measured. This is useful to find since you can repeatedly apply this process until the correct answer has arbitrarily high probability.

With a phase flip oracle like $U_\omega$, we can get the $x$ that is correct to get flipped to negative phase. This makes the average amplitude to be lower, since $x$ has the same magnitude of probability as everything else but $x$ is negative:
![[Pasted image 20240214130324.png]]
There exists an operation $U_S$ that rotates a quantum state around its average. This function is called a **diffuser**.

In general, if a given state has amplitude $\beta$ and the average amplitude is $\alpha$, the new amplitude after applying the diffuser is
$$
\alpha + (\alpha - \beta) = 2\alpha - \beta
$$
In the above example, this would make the state corresponding to $\ket \omega$ rise much higher since it is farther from the average.
![[Pasted image 20240214131119.png]]

# Intuition
Consider $\ket s$ to be the starting superposition of every input. Then, we can define
$$
\ket{s'} = \ket 0 + \ket 1 + \cdots + \ket{\omega - 1} + 0 + \ket{\omega + 1} + \cdots
$$
such that $\ket{s'} \cdot \ket \omega = 0$, which implies that these two basis states are orthogonal and can be used to define a linear system. This means that $\ket s$ can be expressed as a linear combination of the two:
$$
\ket s = \dfrac{\sqrt{N - 1}}{\sqrt N}\ket{s'} + \dfrac{1}{\sqrt N}\ket{\omega}
$$
![[Pasted image 20240219122647.png]]
The angle $\theta$ is equal to $\sin^{-1}\left(\frac{1}{\sqrt{N}}\right)$, since the vector has magnitude 1.
After we apply the phase flip oracle, we reflect across $\ket{s'}$:
![[Pasted image 20240219122834.png]]
Then, we use the diffuser to rotate across $\ket s$:
![[Pasted image 20240219122902.png]]
which gives us an angle of $2\theta + \theta$ away from $\ket{s'}$. Every iteration of these two operations together gives an increase in $2\theta$. Since we want to rotate $\frac{\pi}{2} - \theta$ radians from $\ket s$ to get to $\ket \omega$, the number of iterations we need to do $r$ is
$$
\begin{align*}
2\theta r &= \frac{\pi}{2} - \theta \\
r &=\frac{\pi}{4\theta} -  1 \\
&= \frac{\pi}{4\sin^{-1}\left(\frac{1}{\sqrt{N}}\right)} - 1 \\
&=\frac{\pi\sqrt N}{4} - 1 \\
&=\left\lceil\frac{\pi\sqrt N}{4}\right\rceil \\
\end{align*}
$$
assuming $N$ is very large and ceiling the value because we can only do an integer amount of iterations.

## Diffuser
If a state $\ket v$ is orthogonal to $\ket u$, flipping across $\ket u$ means that $\ket v \to -\ket v$. We can apply this to composite states by just flipping the sign of the coefficient of that state $\ket v$.

Rotating around an arbitrary state like $\ket s$ is difficult though since it would take a lot of work to find all the basis states orthogonal to $\ket s$. It is, however, easy to know all states orthogonal to $\ket {00\cdots0}$, as these are every possible measurement.
We can then rotate around $\ket s$ by:
- Rotating so that $\ket s$ is equal to $\ket 0$ (this is applying a lot of $H$ gates, since that is how we got to $\ket s$)
- Reflecting over all states orthogonal to $\ket 0$
- Rotating so that $\ket 0$ is equal to $\ket s$
![[Pasted image 20240221121805.png]]
Scaling this up to multiple qubits, we need to change our logic so that we are only adding phase to the $\ket {000\cdots0}$ since the pairwise CZ gates would get cumbersome:
![[Pasted image 20240221122233.png]]

# Multiple Solution Grover's Algorithm
If there are $M$ solutions, then the angle that we rotate by is
$$
\theta = \sin^{-1}\left(\dfrac{2\sqrt{M(N - M)}}{N}\right)
$$
which means that we need
$$
r = \left \lfloor \frac{\pi}{4} \sqrt{\frac{N}{M}} \right \rfloor
$$
When we measure after doing rotations, we could get any one of the possible solutions with equal probability. This makes the algorithm not very useful for enumerating every solution.

If $M > N/2$, then Grover's algorithm is not very useful as the approximation for $r$ breaks down. In these cases, it is faster and more reliable to use classical algorithms.

Alternatively, we can add another input bit so that $N = 2N$ while $M = M$.

## Counting Solutions
One issue with this is that we need to know $M$ beforehand so we can determine how many iterations of Grover we should do. In both cases of Grover, doing too many iterations decreases the probability that we measure the correct answer later. In the intuition, this would look like over-rotating.

One way of deriving $M$ is finding $\theta$.