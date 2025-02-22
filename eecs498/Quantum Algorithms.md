Many quantum algorithms work by evaluating some global property of a classical function. We start by creating a superposition of every possible input, then make interference work to filter out the answer we are interested in.
## Quantum Oracle
For an n-bit function, there are $2^{2^n}$ functions that are possible. Classical functions usually aren't reversible, so to use them in quantum circuits, we have to add a second output and input that lets us reverse the operation. Typically, we have inputs $x, y$ and return $x, y \oplus f(x)$ . This way, we can reverse by xoring $f(x)$ again.
- The qubit(s) that contains $x$ are usually called a *data register*.
- The other qubit ($y$) is called the *target register*.
Because the target register gets loaded with $y \oplus f(x)$, we can actually feed the output of a quantum oracle back into itself and get $y$ back.

If you set the target qubit to $\ket 0$, the data register is unmodified. This may flip the bit of the target register, so this is called a bit-flip oracle.
If you set the target register to $\ket -$, the target register stays unmodified and it may flip the phase of the data register. This is called a phase flip oracle.

# Distinguishing States
For any two states to be distinguished in **one measurement**, they must be on opposite sides of the Bloch sphere. This implies that the states have an inner product of 0, and there is some rotation of the Bloch sphere that can move these states to the z-axis.

Most quantum algorithms will try to **encode a global property of a function onto orthogonal states**.

# Quantum Speedup
There are $2^{2^n}$ $n$-bit functions, so a quantum algorithm that can decide some property of a function gives a $\log_2(2^{2^n}) = 2^n$ times speedup.