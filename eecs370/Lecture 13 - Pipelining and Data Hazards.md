The convention for naming pipeline registers is just to combine the two stages the pipeline register connects. Pipeline registers are clocked memory that store anything you might need in the next stage.
> Note that `PC + 1` is usually passed along though its not used in most stages - it still has to get to the end.

Stages in LC2K:
- Fetch
- Decode
- Execute (ALU)
- Memory
- Write back (data sent back to the decode stage)

# Pipelining Issues
- **Data hazards**: register reads occur before register updates - different instructions could read *stale* values.
- **Control hazards**: Branches change the PC, but only after a couple of stages - other instructions have already been read starting from the old PC.
- **Exceptions**: Sometimes programs need to pause and resume (OS management)
## Data Hazards
A **data dependency** is a situation where one instruction depends on the results of another instruction, regardless of how many instructions are between them. A **data hazard** results from not correctly dealing with a **data dependency**.
The following LC2K code has a Read-After-Write dependency (RAW):
```lc2k
add 1 2 3
nor 3 4 5
```
The `nor` instruction tries to read register 3 in the stage right after the add instruction read their registers - the `add` instruction has not yet written back the register value, so `nor` reads the wrong value.

>Note: most registers are designed so that if you are doing a simultaneous read/write on the same register, the read will get forwarded the new value (this is system dependent however)

## Resolutions
- Make sure that machine code never lets this happen (assembler?)
	- breaks backward compatability
	- makes programs larger
	- slow
- build hardware to detect and stall (insert noops until it stops)
	- slow
- build hardware to detect and forward (fix the pipeline to get the correct value)