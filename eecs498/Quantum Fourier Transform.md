In [[Grover's Algorithm]], we had the issue that we needed a way to estimate the number of solutions $M$. This can be done by measuring $\theta$, or how much phase a qubit rotates.

The inverse Fourier transform is something we could possibly use to figure this out.

Consider a new parameterized phase gate which adds $\theta$ phase to a qubit.
$$
P(\theta) = \begin{bmatrix}
1 & 0 \\
0 & e^{i\theta}
\end{bmatrix}
$$
# Quantum Phase Estimation
We use the QFT to estimate how much phase a gate or operation $U$ kicks back. Say we have $n$ qubits to play with. Then, we apply a controlled $U$ on the eigenstate of $U$, with control bit 0. We then apply controlled $U$ twice on the next qubit, and repeat until desired precision ($n$ bits).
We plug this back in to the QFT to get a number proportional to the state change. We divide this number by $2^n$ to get the actual phase.
![[Pasted image 20240311121228.png]]