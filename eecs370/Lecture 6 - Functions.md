Sequencing Instructions change how the program is run (modify the pc). There are two types:
- unconditional branches
- conditional branches
# Conditional Branches
There are two types of conditional branches:
- one type compares a register to 0
The `offsetField` in ARM/LEG is measured in terms of instructions. For example
```armasm
CBZ X1. 25
```
will set the program code to `PC + 100` if `X1` is equal to 0. `CBNZ` branches if the register is *not* equal to 0.
- compare condition codes
ARM has an extra **program status register** to check for various conditions. This register has 4 different flags:
- **N**egative
- **Z**ero
- o**V**erflow
- **C**arry
Any instruction in ARM that ends with `S` will set the flags based on the result. For example, if `ADDS` has a negative result, the `N` flag is set. Condition Codes:

|Encoding|Name (alias)|Meaning (integer)|Flags|
|---|---|---|---|
|`0000`|`EQ`|Equal|`Z==1`|
|`0001`|`NE`|Not equal|`Z==0`|
|`1010`|`GE`|Signed greater than or equal|`N==V`|
|`1011`|`LT`|Signed less than|`N!=V`|
|`1100`|`GT`|Signed greater than|`Z==0 && N==V`|
|`1101`|`LE`|Signed less than or equal|`~(Z==0 && N==V)`|
|`1110`|`AL`|Always|Any|

The `CMP` instruction is a shortcut for `SUBS`, it does a subtract instruction and only sets flags, does not set a result.
```armasm
CMP X1, X2
B.GT Label1
```
will branch to `Label1` if X1 is greater than X2
## Far Branching
Most branch instructions can only branch $2^{19}$ words in memory. If we want to branch farther than that, the assembler will instead invert your condition and use an unconditional branch:
```armasm
	CBZ X15, FarLabel
will be processed as
	CBNZ X15, L1
	B FarLabel
L1:
```
The unconditional branch has a 26 bit offset.
# Unconditional Branching
There are three types of unconditional branches in LEGv8:

|instruction|example|direct|description|
|---|---|---|---|
|branch|`B 2500`|`go to PC + 10000`|Branch to target address; PC-relative|
|branch to register|`BR X30`|`go to X30`|For switch, procedure return|
|branch with link|`BL 2500`|`X30 = PC + 4; go to PC + 10000`|For procedure call, PC-relative|

# Functions
## Passing Parameters
In ARM, the first few parameters passed to a function are put in X1-X7 if they fit, the rest in memory on the call stack.
## Call Stack
A region of memory is allocated for the call stack in most processors. This memory usually contains
- parameters that were not passed through registers
- local variables
- temporary storage (when no more registers)
- return address
- others
## Saving and Restoring
Functions may overwrite registers used by the functions they are called from. This can be prevented by either:
- having the called function save the register values before it overwrites them and restore them before that function returns (**callee** saved)
- having the calling function save the register values before the called function overwrites them and restore them after the function call (**caller** saved)