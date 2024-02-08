The **efficiency** of an algorithm is measured by how it's *worst-case* runtime scales with input size. Input size can be
- \# of elements
- \# of vertices (+) \# of edges
- \# of digits
## Polynomial Time
We can say that something is **efficient** if the runtime is polynomial in size of the input. Brute force algorithms are typically inefficient because they typically involve enumerating all of the input multiple times, which is exponential.
We do not necessarily know that there are polynomial time algorithms for every decidable problem. There are no known solutions to some problems like TSP but it has also not been proven that there does not exist any algorithm that is polynomial time. This is the P ?= NP problem. 
Formally, class **P** is the set of all languages that can be decided by a Turing Machine in polynomial time:
$$
P = \bigcup_{k \ge 1} \text{DTIME}(n^k)
$$

Binary search can be used to convert any algorithm that can verify a solution in polynomial time to one that can search in polynomial time, by binary searching the input space (usually, not always applicable)

## Non-Deterministic Polynomial Time
The other class $NP$ does not stand for Non-Polynomial time. It can be better though of as "Verifiable Problems".
- If a problem has a solution, then there is an efficient way to verify it given some additional information. This information is known as a *certificate*.
- If there is no solution, there is no additional information that would convince us that a solution is true.
A problem is **efficiently verifiable** if there exists an algorithm $V(x, c)$ called a *verifier* such that, where
- $x$ is the input
- $V(x,c)$ is polynomial in terms of the size of $x$
- If $x$ is valid, then there exists some certificate $c$ that will cause $V(x,c)$ to be true
- If $x$ is invalid, then for all $c$, $V(x,c)$ is false
The class $NP$ is the class of all languages such that an efficient verifier exists.
$$NP = \{L : \exists V(x, c), V\text{ is an efficient verifier for }L\}$$
The complement of a language that is efficiently verifiable may or may not be efficiently verifiable. This has to do with how the certificate may need to be restructured.
## P vs NP
P is a subset of NP.