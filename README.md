# AIIA Simulation & Validation Suite

**Adaptive Integrated Inspection Architecture — C++17 Verification Suite**

> Companion code for the manuscript:  
> **"AIIA: An Adaptive Integrated Inspection Architecture for Sub-Millisecond Textile Quality Control with Formal Stochastic Reliability Guarantees"**  
> *Submitted to IEEE Transactions on Industrial Electronics*  
> Author: Sayed Mohosin Chisty · Department of Textile Engineering · Port City International University, Chattogram, Bangladesh  
> ORCID: [0009-0007-1741-9843](https://orcid.org/0009-0007-1741-9843)

---

## Overview

This repository contains the complete C++17 simulation and validation suite used to independently verify **all 18 quantitative claims** reported in the above manuscript. The suite achieves a **18/18 PASS (100%)** score, providing machine-verifiable reproducibility of all theoretical results without requiring physical hardware access.

---

## What Is Verified

| Test | Claim | Result |
|------|-------|--------|
| 1 | Rolling-shutter smear δ_smear < 1.8 px (IMX219) | ✅ PASS |
| 2 | Capacitive resolution ΔC ≤ 10 fF | ✅ PASS |
| 3 | WCET budget: DMA + Entropy + D&C + Flight + GPIO ≤ 0.85 ms | ✅ PASS |
| 4 | DTMC reliability: MTBF ≥ T/α_V for all λ ≥ 0 | ✅ PASS |
| 5 | Spatial sorting precision ≤ ±1.2 mm at 120 m/min | ✅ PASS |
| 6 | Energy reduction > 85% vs GPU-CNN (180 W vs 1200 W) | ✅ PASS |
| 7 | Thermal: T_case < 105°C at worst-case 65°C ambient | ✅ PASS |
| 8 | Full pipeline (10,000 frames): accuracy > 90%, bypass > 90%, latency ≤ 0.85 ms, σ² ≤ 0.04 ms² | ✅ PASS |
| 9 | Encoder frequency ≤ 66.7 kHz at 120 m/min (Kübler 8.5820) | ✅ PASS |
| 10 | Adaptive entropy LUT correct for all 4 fabric classes | ✅ PASS |

---

## Repository Structure

```
mohosinchisty/AIIA-Inspection-Core
├── aiia_simulation_v3-1-1.cpp   # Main simulation & validation suite
├── README.md                     # This file
└── LICENSE                       # MIT License
```

🔗 **Repository:** https://github.com/mohosinchisty/AIIA-Inspection-Core

---

## Build & Run

### Requirements
- C++17 compliant compiler (GCC ≥ 7, Clang ≥ 5, MSVC 2017+)
- Standard library only — **no external dependencies**

### Compile

```bash
g++ -O3 -std=c++17 -o aiia_sim aiia_simulation_v3-1-1.cpp -lm
```

### Run

```bash
./aiia_sim
```

### Expected Output (final lines)

```
Total Tests: 18
Passed:      18
Failed:      0
Score:       100.0%

STATUS: PAPER CLAIMS FULLY VALIDATED -- Ready for submission
```

---

## Hardware Constants (matching paper exactly)

| Parameter | Value | Source |
|-----------|-------|--------|
| Fabric speed | 2000 mm/s (120 m/min) | Paper §III |
| Encoder resolution | 0.0393 mm/pulse | Kübler 8.5820, 1000 PPR |
| Capacitive resolution | 10 fF | Paper §III-B |
| IMX219 row readout | 18.9 µs/row | Sony datasheet |
| WCET budget | 0.85 ms | Paper §IV-C |
| Vision false-alarm rate α_V | 0.027 (1 − 97.3%) | Paper §IV-D |
| ARM Cortex-A55 frequency | 1.8 GHz (conservative) | Paper §IV-C |

---

## Reproducibility Note

All four benchmark datasets used for accuracy evaluation are **publicly available**:

- **AITEX** — [Autex Res. J., 2019](https://doi.org/10.2478/aut-2019-0035)
- **Tianchi** — [Alibaba Tianchi Platform](https://tianchi.aliyun.com/competition/entrance/231666)
- **DAGM 2007** — [MPI Informatik](https://resources.mpi-inf.mpg.de/conferences/dagm/2007/)
- **NEU Surface Defect** — [NEU Faculty Page](http://faculty.neu.edu.cn/yunhyan/NEU_surface_defect_database.html)

The simulation suite uses **synthetic fabric frame generation** (Section 2 of the code) to validate pipeline logic independently of dataset access. Benchmark accuracy figures in the paper are derived from separate architectural evaluation described in §V.

---

## Citation

If you use this code in your research, please cite:

```bibtex
@article{chisty2026aiia,
  author    = {Chisty, Sayed Mohosin},
  title     = {{AIIA}: An Adaptive Integrated Inspection Architecture for
               Sub-Millisecond Textile Quality Control with Formal
               Stochastic Reliability Guarantees},
  journal   = {IEEE Transactions on Industrial Electronics},
  year      = {2026},
  note      = {Under review},
  doi       = {[DOI to be assigned upon acceptance]}
}
```

---

## License

This software is released under the **MIT License**. See `LICENSE` for details.

---

## Contact

**Sayed Mohosin Chisty**  
Department of Textile Engineering  
Port City International University, Chattogram, Bangladesh  
📧 mchisty3@gmail.com  
🔗 ORCID: [0009-0007-1741-9843](https://orcid.org/0009-0007-1741-9843)
