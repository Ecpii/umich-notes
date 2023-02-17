# Performance Metrics
**CPI** is the average numbers of cycles ber instruction. This is dependent on the clock cycle and the mix of instructions used.

# Pipelining
Idea: build a multi cycle processor, line up instructions, and overlap execution.
- Cycle #1: Fetch 1
- Cycle #2: Fetch 2, Decode 1
- Cycle #3: Fetch 3, Decode 2, Execute 1