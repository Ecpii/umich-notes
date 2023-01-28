# Arithmetic
|Description|Assembly|Equivalent|Comments|
|---|---|---|---|
|Add|<nobr>`ADD Xd, Xn, Xm`</nobr>|$X_d = X_n + X_m$|Register to Register|
|Add and set flags|<nobr>`ADDS Xd, Xn, Xm`</nobr>|$X_d = X_n + X_m$|flags NZVC|
|Add immediate|<nobr>`ADDI Xd, Xn, #uimm12`</nobr>|$X_d = X_n + 280$|12 bit unsigned, $[0, 4095]$|
|Add immediate and set flags|<nobr>`ADDIS Xd, Xn, #uimm12`</nobr>|$X_d = X_n + 280$|flags NZVC|
|Subtract|<nobr>`SUB Xd, Xn, Xm`</nobr>|$X_d = X_n - X_m$|Register to Register|
|Subtract and set flags|<nobr>`SUBS Xd, Xn, Xm`</nobr>|$X_d = X_n - X_m$|flags NZVC|
|Subtract immediate|<nobr>`SUBI Xd, Xn, #uimm12`</nobr>|$X_d = X_n - 280$|12 bit unsigned, $[0, 4095]$|
|Subtract immediate and set flags|<nobr>`SUBIS Xd, Xn, #uimm12`</nobr>|$X_d = X_n - 280$|flags NZVC|
See [[Lecture 4 - ARM#Format]] for format.

# Data Transfer
|Description|Assembly|Equivalent|Comments|
|---|---|---|---|
|load register|<nobr>`LDUR Xt, [Xn, #simm9]`</nobr>|$X_t = \text{mem}[X_n, 203]$|`#simm9` is a signed integer with 9 bits, `[-256, 255]`|
|load signed word|<nobr>`LDURSW Xt, [Xn, #simm9]`</nobr>|$X_t = \text{mem}[X_n, 203]$|load into lower 32b, **sign extend** upper 32b|
|load half|<nobr>`LDURH Xt, [Xn, #simm9]`</nobr>|$X_t = \text{mem}[X_n, 203]$|load into lower 16b, *zero extend* upper 48b|
|load byte|<nobr>`LDURB Xt, [Xn, #simm9]`</nobr>|$X_t = \text{mem}[X_n, 203]$|load into lower 8b, *zero extend* upper 56b|
|store register|<nobr>`STUR Xt, [Xn, #simm9]`</nobr>|$\text{mem}[X_n, 203] = X_t$||
|store word|<nobr>`STURW Xt, [Xn, #simm9]`</nobr>|$\text{mem}[X_n, 203] = X_t$|store lower 32b|
|store half|<nobr>`STURH Xt, [Xn, #simm9]`</nobr>|$\text{mem}[X_n, 203] = X_t$|store lower 16b|
|store byte|<nobr>`STURB Xt, [Xn, #simm9]`</nobr>|$\text{mem}[X_n, 203] = X_t$|store lower 8b|
|move wide with zero|<nobr>`MOVZ Xd, #uimm16, LSL N`</nobr>|$X_d = \text{0b}0\ldots0N0\ldots0$|zeros out Xd and place the unsigned integer in the first (N = 0), second (N = 16), third (N = 32), or fourth (N = 48) slot of Xd
|move wide with keep|<nobr>`MOVK Xd, #uimm16, LSL N`</nobr>|$X_d = \text{0b}x\ldots xNx\ldots x$|same as above but keeps the original other bits|
For more on loading/saving, see [[Lecture 4 - ARM#Memory Instructions]] and [[Lecture 5 - Memory Alignment]].

# Logical Operations
|Description|Assembly|Equivalent|Comments|
|---|---|---|---|
|and|<nobr>`AND Xd, Xn, Xm`</nobr>|$X_d = X_n \mathrel \& X_m$|bitwise and|
|and immediate|<nobr>`ANDI Xd, Xn, #uimm12`</nobr>|$X_d = X_n \mathrel \& 280$|with 12 bit unsigned $[0, 4095]$|
|inclusive or|<nobr>`ORR Xd, Xn, Xm`</nobr>|$X_d = X_n \mathrel | X_m$|bitwise or|
|inclusive or immediate|<nobr>`ORRI Xd, Xn, #uimm12`</nobr>|$X_d = X_n \mathrel | 280$|with 12 bit unsigned $[0, 4095]$|
|exclusive or|<nobr>`EOR Xd, Xn, Xm`</nobr>|$X_d = X_n \mathrel \wedge X_m$|bitwise xor|
|exclusive or immediate|<nobr>`EORI Xd, Xn, #uimm12`</nobr>|$X_d = X_n \mathrel \wedge 280$|with 12 bit unsigned $[0, 4095]$|
|logical shift left|<nobr>`LSL Xd, Xn, #uimm6`</nobr>|$X_d = X_n << 3$|shift left by a constant $[0, 63]$|
|logical shift right|<nobr>`LSR Xd, Xn, #uimm6`</nobr>|$X_d = X_n >> 3$|shift right by a constant $[0, 63]$|

# Branching
For more on this, see [[Lecture 6 - Functions]]
## Unconditional Branches
|Description|Assembly|Extended Description|
|---|---|---|
|branch|<nobr>`B #simm26`</nobr>|Branch to PC + the 26 bit signed number given * 4 (since byte addressable)|
|branch to register|<nobr>`BR Xt`</nobr>|Branch to the address stored in Xt|
|branch with link|<nobr>`BL #simm26`</nobr>|Branch as with `B`, but store the return address in X30|
## Conditional Branches
|Description|Assembly|Extended Description|
|---|---|---|
|conditional branch = 0|<nobr>`CBZ Xt #simm26`</nobr>|Branch to PC + the 19 bit signed number given * 4 (since byte addressable) **if** register Xt == 0|
|conditional branch != 0|<nobr>`CBNZ Xt #simm26`</nobr>|Branch to PC + the 19 bit signed number given * 4 (since byte addressable) **if** register Xt != 0|
|conditional branch|<nobr>`B.cond #simm26`</nobr>|Branch to PC + the 19 bit signed number given * 4 (since byte addressable) **if** `cond` is true|
### Conditional Cases (cond)
|Condition|Code|Signed Number|Unsigned|Description|
|---|---|---|---|---|
|$=$|`EQ`|`Z == 1`|`Z == 1`|equal|
|$\ne$|`NE`|`Z == 0`|`Z == 0`|not equal|
|$<$|`LT`/`LO`|`N != V`|`C=0`|less than|
|$\le$|`LE`/`LS`|`~(Z==0 & N==V)`|`~(Z==0 & N==V)`|less than or equal|
|$>$|`GT`/`HI`|`(Z==0 & N==V)`|`(Z==0 & C==1)`|greater than|
|$\le$|`GE`/`HS`|`N == V`|`C == 1`|greater than or equal|
# Pseudoinstructions
`MOV Xd, Xn` is the same as `ORR Xd, XZR, Xn` for copying registers
`CMP Xn, Xm` is the same as `SUBS XZR, Xn, Xm` but without storing into register
`CMPI` same as above but with immediate