# Base + Displacement Memory Finding
The most common method for finding things in memory is to keep the base address of an object in a register and add a displacement to this address to find the other objects in memory related to this object.
```asm
load r1, mem[r2 + 32]
```
# PC-relative addressing
Same as base + displacement, but the base is now the Program Counter.
```
jump [-8]
```
will jump back 2 instructions (32 bit instructions)
# ISA Types
RISC (Reduced Instruction Set Computing)
- fewer instructions
- encoding of instructions usually same size
- simple hardware
- larger programs
- LC2K, RISC-V, ARM
CISC (Complex Instruction Set Computing)
- more instructions
- encoding may be different sizes
- complex hardware
- short programs
- x86
# LC2K
## Instruction Format
**Register Instructions**:
| 31-25    | 24-22      | 21-19    | 18-16    | 15-3     | 2-0       |
| -------- | ---------- | -------- | -------- | -------- | --------- |
| *unused* | **opcode** | **regA** | **regB** | *unused* | **destR** |

**Immediate Instructions**
| 31-25    | 24-22      | 21-19    | 18-16    | 15-0       |
| -------- | ---------- | -------- | -------- | ---------- |
| *unused* | **opcode** | **regA** | **regB** | **offset** |

**J-type instructions**
| 31-25    | 24-22      | 21-19    | 18-16    | 15-0     |
| -------- | ---------- | -------- | -------- | -------- |
| *unused* | **opcode** | **regA** | **regB** | *unused* |

**O-type instructions**
| 31-25    | 24-22      | 21-0     |
| -------- | ---------- | -------- |
| *unused* | **opcode** | *unused* |
