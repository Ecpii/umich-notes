To determine whether a function is constant or balanced, we can put $H$ gates on each of the data bits to a register so that all the inputs are $\ket +$ and the control input is $\ket -$. Then $H$ all of the input bits after the oracle, if any of them are non-zero the function is not constant.
![](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/Deutsch-Jozsa-algorithm-quantum-circuit.png/800px-Deutsch-Jozsa-algorithm-quantum-circuit.png)

If fed a non-balanced, non-constant function, the algorithm is no longer deterministic and can output anything.

An intuition for this is that since the control qubit is in the $\ket -$ state, which is an eigenstate on the $X$ gate, there will be phase kickback if $f(x)$ is not constant.