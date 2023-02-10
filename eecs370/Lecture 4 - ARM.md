# Format
Destination register is usually the first register in an instruction.
```arm
ADD X3, X4, X7 // X3 = X4 + X7
```
For example, the following two codes are the same:
```c
f = (g + h) - (i + j)
```
```arm
ADD X1, X3, X4
ADD X2, X5, X6
SUB X7, X1, X2
```
Instruction bitwise format:

| opcode  | Rm                      | shamt        | Rn                     | Rd                   |
| ------- | ----------------------- | ------------ | ---------------------- | -------------------- |
|         | second register operand | shift amount | first register operand | destination register |
| 11 bits | 5 bits                  | 6 bits       | 5 bits                 | 5 bits               |

## Immediate Instructions
The second source can be a register or an **i**mmediate (a constant in the instruction).
```arm
ADD X3, X4, #10 // different from the previous ADD opcode, #10 is a constant 10
```

| opcode  | immediate    | Rn                            | Rd                   |
| ------- | ------------ | ----------------------------- | -------------------- |
|         | unsigned int | first register operand amount | destination register |
| 10 bits | 12 bits      | 5 bits                        | 5 bits               |

## Logical Instructions
`AND`, `OR`, `XOR`, `NOT` are logical instructions you can use in ARM.
## Shift Instructions
```arm
LSL X6, X23, #2 // this is the same as
```
```c
X6 = X23 >> 2;
```
The source register `X23` is not modified here. In shift operations `Rm` is always 0, `shamt` is stored as a 6 bit unsigned integer.
## Pseudo Instructions
Some assemblers have shorthand mnemonics that translate to different instructions. For example, the two following lines are the same:
```
MOV X12, X2
ORR X12, XZR, X2
```
## Memory Instructions
ARM is byte addressable, LC2K is word addressable. A word is 4 bytes.
In ARM/LEG, registers are 64 bits wide. When loading in data smaller than this, we have two options for how to fill the rest of the bits:
- set to zero: may lose sign on signed numbers
- sign extend: take most significant bit of previous number and just fill the space with it

| Desired amount of data | Operation                        | Unused bits |
| ---------------------- | -------------------------------- | ----------- |
| 64 bits                | LDUR (load unscaled to register) | N/A         |
| 16 bits                | LDURH                            | set to zero |
| 8 bits                 | LDURB                            | set to zero |
| 32 bits                | LDURSW (load signed word)        | Sign extend |
