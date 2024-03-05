In [[Grover's Algorithm]], we had the issue that we needed a way to estimate the number of solutions $M$. This can be done by measuring $\theta$, or how much phase a qubit rotates.

The inverse Fourier transform is something we could possibly use to figure this out.

Consider a new parameterized phase gate which adds $\theta$ phase to a qubit.
$$
P(\theta) = \begin{bmatrix}
1 & 0 \\
0 & e^{i\theta}
\end{bmatrix}
$$