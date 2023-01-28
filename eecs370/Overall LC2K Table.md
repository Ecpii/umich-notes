- 8 registers $[0, 7]$
- Addresses are 32-bit
- Word-addressable (a word is 4 bytes/32 bits)
- 65536 words of memory
- r0 is always 0

|Name|Type|Opcode|Action|
|---|---|---|---|
|`add`|R|0b000|Add contents of `regA` with `regB`, store in `destReg`.|
|`nor`|R|0b001|Nor contents of `regA` with `regB`, store in `destReg`.|
|`lw`|I|0b010|Load `regB` from address `[regA + offsetField]`.|
|`sw`|I|0b011|Store `regB` to address `[regA + offsetField]`.|
|`beq`|I|0b100|If `regA == regB`, branch to `PC + 1 + offsetField`.|
|`jalr`|J|0b101|Store `PC+1` in `regB`, jump to `regA`.|
|`halt`|O|0b110|Stop program.|
|`noop`|O|0b111|Do nothing.|

# Anatomy of Instruction
## R-Type
`opcode regA regB destReg`
|Bits|31-25|24-22|21-19|18-16|15-3|2-0|
|---|---|---|---|---|---|---|
|Description|*unused*|**opcode**|**regA**|**regB**|*unused*|**destR**|

## I-Type
`opcode regA regB offsetField`
|Bits|31-25|24-22|21-19|18-16|15-0|
|---|---|---|---|---|---|
|Description|*unused*|**opcode**|**regA**|**regB**|**offset**|

## J-Type
`jalr regA regB`
|Bits|31-25|24-22|21-19|18-16|15-0|
|---|---|---|---|---|---|
|Description|*unused*|**opcode**|**regA**|**regB**|*unused*|

## O-Type
`opcode`
|Bits|31-25|24-22|21-0|
|---|---|---|---|
|Description|*unused*|**opcode**|*unused*|