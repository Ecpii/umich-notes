CNOT is the following gate, which can also be thought of as XOR with passthrough:
$$
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 1 & 0 \\
0 & 1 & 0 & 0
\end{bmatrix}
$$
On a two qubit circuit, it designates one qubit as a "control bit" and the other as a "target bit". If the control bit is 1, the target qubit is flipped. The following is the truth table:

| Input (target, control) | Output (target, control) |
| ----------------------- | ------------------------ |
| `00`                    | `00`                     |
| `01`                    | `11`                     |
| `10`                    | `10`                     |
| `11`                        | `01`                         |
## Important Examples
The CNOT of $|0\rangle$ and $|+\rangle$ is the **Bell State**, or the maximum entangled state:
$$
\text{CNOT}\ |0 +\rangle = |00\rangle + |11\rangle
$$
where $|+\rangle$ is the control qubit. There is no such pair of qubits $\ket{a}, \ket b$ that
$$
\ket{ab} = \ket{a} \otimes \ket{b} = \ket{00} + \ket{11}
$$
In fact, there is a distinction between all the states possible by multiplying two independent qubit states and those like the Bell State. The former are called **product states**, and everything else is an **entangled state**. There are far more entangled states than product states as you have more qubits in a system.

Entangled states mean that the probabilities of the qubits are correlated in some way.

### Eigenstate $\ket{++}$
Every gate has some circuit that will not change (eigenstates). $\ket{++}$  is one of them for CNOT:
$$
\text{CNOT}\ \ket{++} = \ket{++}
$$
### $\ket{-+}$
In this case, even though $\ket +$ was the control qubit, it got flipped to $\ket -$
$$
\begin{align*}
\ket{-+} &= \ket{00} + \ket{01} - \ket{10} - \ket{11} \\
\text{CNOT }\ket{-+} &= \ket{00} + \ket{11} - \ket{10} - \ket{01} \\
&= (\ket{0} - \ket{1}) \otimes(\ket{0} - \ket{1}) \\
&= \ket{--}
\end{align*}
$$
In fact, if you run CNOT on $\ket{--}$, you get $\ket{-+}$. This phenomenon is called **phase kickback**.
## Phase Kickback
Some states that do not move when a gate is applied to them are called **eigenstates**, with optional added phase, called an **eigenvalue**. For example, the $X$ gate has $\ket +$ and $\ket -$ as eigenstates:
- $X\ket + = X(\ket 0 + \ket 1) = \ket 1 + \ket 0 = \ket +$
- $X\ket - = X(\ket 0 - \ket 1) = \ket 1 - \ket 0 = -\ket -$
A controlled-U (CU) operation is one where $U$ is applied to a target qubit if a control qubit is 1. Let $\ket \lambda$ be an eigenstate of $U$ with eigenvalue $e^{i\theta}$. Then,
$$
CU\ket{\lambda +} = \ket{\lambda} \otimes \left(\ket 0 + e^{i\theta} \ket 1\right)
$$
The idea behind this is that there is only added phase on the $\ket 1$ state because the gate only activates when the control qubit is a 1.
Generally, in phase kickback, the target qubit stays the same, and the control qubit rotates $\theta$ radians around the z-axis.