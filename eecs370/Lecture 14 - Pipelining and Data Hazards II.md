# Detecting Data Hazards
Keep a queue (known as a shift register) of registers, compare regA and regB to these registers each time

## Detect & Stall:
- block the previous pipeline register (before decode) from updating if a hazard is detected (using the enable signal of the register)
- block the pc register from updating too
## Detect & Forward:
- instead of stalling the decode stage, we can add more paths so that we can just return the value to where its needed when its needed
- this means we have to pass in the hazard to each pipeline register so we can change muxes accordingly
- there are different ways we want to handle hazards based on how far the hazards are away
# Contorl Hazards
## Detect & Stall:
Instead of passing noops into the execute stage, we pass noops to the decode stage. Insert one more noop after you rewrite to PC because of clock shenanigans.