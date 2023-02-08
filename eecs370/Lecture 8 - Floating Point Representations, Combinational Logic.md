# Floating Point Arithmetic
Different approaches to representing real numbers:
- rational numbers (two integers for each number)
annoying to work with, calculations involve shifting bases and all that
- fixed point (allocate a certain number of bits for before/after the decimal point)
not always easy to pick the right units, different scaling factors would be used for different parts of computation
- scientific notation
what is used is the IEEE standard.
## IEEE 754
A single precision floating point number is represented as such:
| |Sign Bit|Exponent|Mantissa/Significand|
|---|---|---|---|
|Description|0 = positive, 1 = negative|The power of 2 to multiply the mantissa by|The 23 most significant bits after the binary point|
|Bits|31|30-23|22-0|

The exponent uses **biased base 127 encoding**, which means that you subtract 127 from the value of the exponent. The range of values here is $[-126, 127]$

![[Pasted image 20230131191758.jpg]]
## Conversion
When converting a decimal number to an IEEE 754 number, we take the most significant bit of the mantissa to be $2^{-1}$, the next most significant bit to be $2^{-2}$, etc. Thus, $10.625_{10} = 1010.101_{2}$.
Once you convert a number to this binary format, you need to normalize the number by shifting the binary point until there is only one bit to the left of the point. As such, $1010.101_2 = 1.010101_2 * 2^3$
We know that the first bit to the left of the point is a 1, so we don't store it. We store the exponent of the 2 in the exponent portion of the format, and as such our conversion is
$$
10.625_{10} = 0\ 10000010\ 01010100000000000000000_2
$$
## Addition Notes
You may lose precision when adding floats because they are normalized to the same base when you add two numbers together, and you may end up running out of bits to represent them. This is largely unavoidable. IEEE 754 also defines a double precision number (a `double`) which has 64 bits, using the same logic as the single precision number defined above. You get 53 bits of precision with a `double`, while the most accurate physical values known are at only 47 bits of precision.

![[Pasted image 20230131193343.png]]

# Combinational Logic
Everything in digital logic is a transistor, which is something that is either on or off. Really small, really fast.
Symbol:

![[Pasted image 20230131221333.png]]

A high voltage makes the transistor act as a wire, a low voltage makes it act like an open switch.
A bubble at the end of a logic gate means to invert the output. 

## Multiplexor
A **multiplexor** or mux is a circuit that can select between two inputs (like an if statement)

![[Pasted image 20230131221938.png]]

You can technically make any circuit using muxes.
## Addition
Doing addition on two bits has the following truth table:
|A|B|C|S|
|---|---|---|---|
|0|0|0|0|
|0|1|0|1|
|1|0|0|1|
|1|1|1|0|

The logic gate for this is:

![[Pasted image 20230131222524.png]]
This is called a half-adder, since it takes in two bits (doesn't account for the carry in bit).

|A|B|Cin|Cout|S|
|---|---|---|---|---|
|0|0|0|0|0|
|0|0|1|0|1|
|0|1|0|0|1|
|0|1|1|1|0|
|1|0|0|0|1|
|1|0|1|1|0|
|1|1|0|1|0|
|1|1|1|1|1|

![[Pasted image 20230131222743.png]]

To add a big number, you can chain these full adders together:

![[Pasted image 20230131223324.png]]

To turn the above into subtraction, you can invert all of the inputs for one color (either all the As or all the Bs), and then give the initial carry bit a 1. This has the effect of making one of the numbers negative (inverting and adding 1).

## Decoder
A decoder will take in an N bit number and output $2^N$ outputs such that exactly one output bit is high.
## Propagation Dleay
Gate outputs do not change exactly when inputs do, because of transmission delay and time for the gate to change (saturation time). Delays between gates will compound.

## Arithmetic Logic Unit
In LC2K, our only two arithmetic operations are `add` and `nor`. We can built a circuit to do all of these things: it will `add` will S is 0 and `nor` when S is 1:

![[Pasted image 20230131230917.png]]