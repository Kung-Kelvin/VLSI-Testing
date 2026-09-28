# VLSI-Testing
VLSI testing research repository (From Oct 2025-March 2026)

This repository will have the resources used for the VLSI testing and the required laboratories by prof. Wen and prof. Stefan

# Updating required (Oct-2025)
When running './2_make_random_tests.py' I get error "AttributeError: `np.unicode_` was removed in the NumPy 2.0 release. Use `np.str_` instead."
In order to run the python script. Had to change the code as suggested `np.unicode_` to `np.str_`

# Running [stuck_at_fault_simulator](./fsim-contest.github/fsim-contest.github/3_stuck_at_fault_simulator.py)
If running from terminal, it must include the bench and test as arguments for example if making bench and test for c17 circuit, the code should be as follows: 

```
python3 ../3_stuck_at_fault_simulator data.nogit/c17.bench data.nogit/c17.tests
```
# Verification scripts before programing
1. A python script was wrote in [testing.ipynb](./fsim-contest.github/fsim-contest.github/testing.ipynb) to verify the information from the bench files.
 - Verify the # of inputs, output, and logic gates in each bench file (compare the comment with the actual ammount of gates)
   - Some discrepancies were found 


| File | Bench comment info (INPUT) | Bench rows info (INPUT) | Test rows info(INPUT) | Bench comment info(OUTPUT) | Bench rows info(OUTPUT) | Test rows info(OUTPUT) | 
|---|---|---|---|---|---|---|
| c880 | 60 | 60 | 60 | 26 | 26 | 26 | 
| c432 | 36 | 36 | 36 | 7 | 7 | 7 | 
| c1355 | 41 | 41 | 41 | 32 | 32 | 32 | 
| c7552 | 207 | 207 | $${\color{red}208}$$ | 108 | 108 | $${\color{red}107}$$ | 
| c17 | 5 | 5 | 5 | 2 | 2 | 2 | 
| c3540 | 50 | 50 | 50 | 22 | 22 | 22 | 
| c6288 | 32 | 32 | 32 | 32 | 32 | 32 | 
| c2670 | 233 | 233 | $${\color{red}309}$$ | 140 | 140 | $${\color{red}64}$$ | 
| c5315 | 178 | 178 | 178 | 123 | 123 | 123 | 
| c1908 | 33 | 33 | 33 | 25 | 25 | 25 | 
| c499 | 41 | 41 | 41 | 32 | 32 | 32 | 
2. After manually reviewing the bench files, **ALL** gates only have one output.
 - For operations for the logic gate, I can ignore the order, prioritize the operation
 - **pending confirmation from prof. Stephan** The order of operation will be from top to bottom on the bench file
3. After manually reviewing the test files, I found the following
 - it's a string of 0/1 followed by '--'(the # of hyphes is the number of outputs)
   - some discrepancies were found
4. Larger circuits to test from [polito](https://github.com/cad-polito-it/I99T)
## Diagrams for concept familiarization. 
Based on the previous information. A simple diagram was drawn using [Wokwi](https://wokwi.com/). This diagram was based on [C17 bench](./fsim-contest.github/fsim-contest.github/data.nogit/c17.bench) information

[Diagram link](https://wokwi.com/projects/444225106610273281)

# Programming 
## "Correct" run
Given the data structure in the bench file and the data in test file a `dict()` will be used as following
`dict[key]=corresponding bit position from the bench file`\
`dict[value]=assigned value from test file or result of the logic operation`

### Logic gates

Information was obtained from this [link](https://www.geeksforgeeks.org/python/logic-gates-in-python/)

| Logic gate | Python operator/Expresion | Conditions |
| --- | --- | --- |
| NAND | `result = 0 if a&b else 1` | 
| AND | `a & b` |
| OR | `a \| b` |
| NOT | `result= 1 if a==0 else 0` | only accepts one input |
| NOR | `result = 0 if a\|b else 1 ` |
| BUFF | `result = a`| only accepts one input |
| XOR | `a ^ b` |
| XNOR | `result = 1 if a==b else 0`|

In the case of 3 or more inputs, a recursion will be used as follow
`6 = NAND (1,2,3,4,5)`\
`6 = NAND (NAND (NAND (NAND (1,2),3),4),5)`

### Coding
**Last update October 8,2025**
two functions have been coded in [program](./fsim-contest.github/fsim-contest.github/3_stuck_at_fault_simulator(Kelvin_tryout).py)

`def logic_gate:` This function has the behavior of the logic gates, as explain in the previous section

`def read_bench:` This function reads the overall information of the circuit.
- primary inputs
- primary outputs
- interconnected signals
- logic gate inputs and outputs

`def read_test:` This function reads the data of the circuit and executes the "correct" behavior

**pending**
- run stuck-at faults model
- compare output between "correct" and stuck-at fault model


## master prompt for python code generation
```
You are an expert Python developer and VLSI testing simulation architect. We are designing a lightweight research prototype to evaluate a custom, criticality-weighted testing and ATPG approach using the ISCAS c880 ALU benchmark circuit.

Your goal is to help me design and write modular Python scripts for the following workflow:
1. Circuit Representation: Parse or structurally model the c880 netlist (using NetworkX or a custom gate-level structure).
2. Golden Functional Simulation: Run baseline functional simulations of the ALU to establish the correct expected Primary Output (PO) behavior.
3. Fault Injection & Weighting Framework: Implement a mechanism to inject single stuck-at faults (SAF), propagate them, and compute a fault weight based on:
   - Approach 1: Random Vector baseline ATPG.
   - Approach 2.1: Weighted approach with uniform PO weights.
   - Approach 2.2: Custom PO weights and ECC-aware metrics (where uncorrectable/high-deviation errors are heavily prioritized).
4. Resource Profiling: Track computational metrics during generation and application phases—specifically measuring CPU time, peak RAM usage, and vector generation efficiency (using libraries like `tracemalloc` or `time`).

Let's build this step-by-step. Start by outlining the project architecture and writing a clean script to parse/model the c880 netlist and run the golden simulation baseline.
```

## master prompt for research 
```
You are an expert academic researcher in VLSI testing, design-for-testability (DFT), and functional safety (e.g., ISO 26262 compliance). 

I am investigating a research hypothesis and need you to search for academic papers, industrial whitepapers (such as Siemens Tessent's Total Critical Area / TCA-weighted ATPG), or IEEE publications that objectively evaluate or discuss the following approach:
- Combining structural fault models (like stuck-at faults) with functional criticality and Error Correction Code (ECC) masking awareness.
- Assigning specific weights to Primary Outputs (POs) and internal circuit faults to represent the severity of error deviation from a golden scenario.
- Guiding or prioritizing ATPG test generation and vector selection based on these custom fault/PO criticality weights rather than treating all faults or outputs equally.

Please provide:
1. Specific academic keywords or sub-fields where this research resides (e.g., risk-based ATPG, defect-oriented testing, application-aware test optimization).
2. Real-world precedents or commercial equivalents (e.g., Critical Area-based ATPG).
3. Key theoretical pros and cons (e.g., how prioritizing high-weight faults affects test pattern compaction versus missing random "low-weight" structural defects).
4. Suggestions for standard metrics used in literature to prove or disprove the efficacy of such a weighted approach over standard random or uniform ATPG.
```
