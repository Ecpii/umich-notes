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
