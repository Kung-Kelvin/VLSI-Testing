# C880 circuit baseline
[Circuit info](https://tumbleweed.nu/r/iscas.restore/doc/trunk/c880.html)

- 60 Inputs
- 26 Outputs
- 383 gates
  - 26 buffers
  - 63 NOTs
  - 117 ANDs
  - 87 NANDs
  - 29 ORs
  - 61 NORs
- 125 fanout stems
- 995 fanout lines
## Bus translation
|I/O buses|Function|ISCAS-85 Netlist numbers|
|---|---|---|
A[8:0]|Main A bus|268,91, 96, 101, 106, 111, 116, 121, 126|
B[7:0]|Main B bus|159, 165, 171, 177, 183, 189, 195, 201|
C[25:0]|Control bus|207, 135, 156, 90, 89, 88, 87, 86, 85, 80, 75, 74, 73,72, 68, 59, 55, 51, 42, 36, 29, 26, 17, 13, 8, 1|
D[3:0]|4-bit bus|143, 146, 149, 153|
F[7:0]|Output function|878,879,880,874,863,864,865,850|
G[3:0]|4-bit bus|8, 51, 17, 152|
C in|Carry in|261|
C8|Carry out|866

## Simulations results
$$fsim performance = \frac{gates *faults *patters}{seconds}$$
### Case 1 (fsim baseline)
```
# 0000000.589 W Cuda unavailable. Falling back to pure Python.
# 0000004.441 - loading ../../fsim-contest.github/fsim-contest.github/data.nogit/c880.bench ...
# 0000004.485 - circuit stats={'node': 826, 'cell': 383, 'fork': 443, 'io': 86, 'line': 1112, 'comb': 383, 'dff': 0, 'latch': 0, 'seq': 0}
# 0000004.489 - line role stats={'lout': 1112}
# 0000004.512 - fault sites: 834
# 0000004.512 - uncollapsed stuck-at fault count: 1668
# 0000004.512 - collapsed stuck-at fault count: 850
# 0000004.516 - FFR count: 151
# 0000004.518 - FFR set stats:
# 0000004.518 - [part] [size] [reach] [prop avg.]
# 0000004.518 - [all]    151     151    0.104
# 0000004.518 - [  0]    151     151    0.104
# 0000004.547 - simple safsim.sim={name: "../../fsim-contest.github/fsim-contest.github/data.nogit/c880.bench", sims: 1024, c_bytes: 150e3}
# 0000044.420 - safsim.timers={startup: 37.45, sim: 2.42, sim_eval2: 0.67}
# 0000044.420 - fsim performance: 1.38e+08 gfp/s
# 0000044.420 - detected by simulation (collapsed): 832/850  -  97.88%
```

### Case 2 (All POs weight = 1)
**only entered 140 vectors**
```
# 0000000.316 W Cuda unavailable. Falling back to pure Python.
# 0000002.453 - loading ../../fsim-contest.github/fsim-contest.github/data.nogit/c880.bench ...
# 0000002.476 - circuit stats={'node': 826, 'cell': 383, 'fork': 443, 'io': 86, 'line': 1112, 'comb': 383, 'dff': 0, 'latch': 0, 'seq': 0}
# 0000002.479 - line role stats={'lout': 1112}
# 0000002.492 - fault sites: 834
# 0000002.492 - uncollapsed stuck-at fault count: 1668
# 0000002.492 - collapsed stuck-at fault count: 850
# 0000002.494 - FFR count: 151
# 0000002.495 - FFR set stats:
# 0000002.495 - [part] [size] [reach] [prop avg.]
# 0000002.495 - [all]    151     151    0.104
# 0000002.495 - [  0]    151     151    0.104
# 0000002.495 - loading ../../fsim-contest.github/fsim-contest.github/data.nogit/c880.tests ...
# 0000002.515 - simple safsim.sim={name: "../../fsim-contest.github/fsim-contest.github/data.nogit/c880.bench", sims: 140, c_bytes: 21e3}
# 0000024.033 - safsim.timers={startup: 20.98, sim: 0.54, sim_eval2: 0.10}
# 0000024.033 - fsim performance: 8.43e+07 gfp/s
# 0000024.033 - detected by simulation (collapsed): 818/850  -  96.24%
```

### Case 3 (Customs POs)
**only entered 62 vectors**
```
# 0000000.330 W Cuda unavailable. Falling back to pure Python.
# 0000002.396 - loading ../../fsim-contest.github/fsim-contest.github/data.nogit/c880.bench ...
# 0000002.420 - circuit stats={'node': 826, 'cell': 383, 'fork': 443, 'io': 86, 'line': 1112, 'comb': 383, 'dff': 0, 'latch': 0, 'seq': 0}
# 0000002.422 - line role stats={'lout': 1112}
# 0000002.435 - fault sites: 834
# 0000002.435 - uncollapsed stuck-at fault count: 1668
# 0000002.435 - collapsed stuck-at fault count: 850
# 0000002.437 - FFR count: 151
# 0000002.438 - FFR set stats:
# 0000002.438 - [part] [size] [reach] [prop avg.]
# 0000002.438 - [all]    151     151    0.104
# 0000002.438 - [  0]    151     151    0.104
# 0000002.439 - loading ../../fsim-contest.github/fsim-contest.github/data.nogit/c880.tests ...
# 0000002.460 - simple safsim.sim={name: "../../fsim-contest.github/fsim-contest.github/data.nogit/c880.bench", sims: 62, c_bytes: 9e3}
# 0000023.952 - safsim.timers={startup: 21.06, sim: 0.43, sim_eval2: 0.07}
# 0000023.952 - fsim performance: 4.67e+07 gfp/s
# 0000023.952 - detected by simulation (collapsed): 796/850  -  93.65%
```