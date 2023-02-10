Everything before this was **combinational logic**, which only takes in conditions. We now need to figure out how to store state, how to *remember* what happened before.

The key to using gates to remember is **feedback** - we feed the outputs of previous operations backwrds.

# SR Latch
The following circuit takes advantage of how `0 nor x` is `not x`, and `1 nor x` is `0`:
![[Pasted image 20230202151241.png]]

## Truth Table

| S   | R   | Q   | Q-  |
| --- | --- | --- | --- |
| 0   | 0   | Q   | Q   |
| 0   | 1   | 0   | 1   |
| 1   | 0   | 1   | 0   |
| 1   | 1   | 0   | 0   |

## Modes
- set (S=1, R=0), q is set to 1
- reset (S=0, R=1), q is set to 0
- latch (S=0, R=0), it latches on the previous value


# Improved SR Latch (D Latch)
In our original SR Latch, if S and R are both 1, then set to 0, the nor gates will keep switching the outputs back and forth. It becomes an unstable circuit.

To fix this, we configure `and` gates in front of the inputs such that `R` and `S` are never the same:

![[Pasted image 20230202152526.png]]

## Truth Table
| D   | G   | R   | S   | Q   | Q-  |
| --- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | Q   | Q-  |
| 1   | 0   | 0   | 0   | Q   | Q-  |
| 0   | 1   | 1   | 0   | 0   | 1   |
| 1   | 1   | 0   | 1   | 1   | 0   |

D can be thought of as "data" or "delay"
G is often called a "gate" because when it is 0 it gets latched

Simply put, the behavior is:
- Q mimics D when G is 1
- when G is 0, ignore what D does and keep the value Q had when G droppet
## Making a PC Counter with a D Latch

![[Pasted image 20230202153911.png]]

# D Flip-flop
The above circuit is very sensitive to the value of G. If it is high for too long, we may increment too many times. If it is high for not long enough, it won't increment at all.
## Clock Signal
A clock signal is simply a signal that switches between 1 and 0 at a fixed frequency. The time a clock changes its signal is known as the edge of the clock. To solve our problem above, we attach two D latches to each other with the gating signal inverted on each one:

![[Pasted image 20230202154352.png]]

The intuition behind this is that the data will never change immediately on the output of the second D latch when the data changes for the input of the first D latch. Q will only update on the rising edge of the clock in this setup.

The only bad thing is if the data is changing at the instant the clock changes. If this happens too often, we need to adjust the clock speed.

Additionally, there is an "enabled d flip flop". This is the same as the flip flop, but with an addition `en` input. If `en` is high, we listen to the clock. If `en` is low, we ignore the clock.

# Finite State Machines
An FSM consists of 
- K states
- N inputs
- M outputs
A transition function matches each current state and input to the next state.
An output function takes in state and/or input to give an output. A **Moore machine** relies only on the states, and a **Mealy machine** relies on both.

The basic structure of an FSM is:

![[Pasted image 20230202161610.png]]

# Read Only Memory
You can implement combinational logic/truth tables by just storing the outputs in read only memory. Take your inputs, then index into that memory using the inputs as an "address".

## Variants
- ROM is non-volatile (doesn't need power to save values).
- Programmable Read Only Memory is ROM that can be written exactly once
- Electronically Erasable PROM can resetted to write to it again.
The size of a ROM is
$$
2^{n_{\text{input}}} * n_{\text{output}}
$$
where $n_{\text{input}}$ and $n_{\text{output}}$ are the number of input and output bits respectively.