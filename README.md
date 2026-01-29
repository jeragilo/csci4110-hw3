# CUDA-Accelerated Particle Simulation (HPC Project)

This repository implements and benchmarks a **particle simulation accelerated with CUDA**,
focusing on **GPU parallelization, memory access patterns, and performance scaling**
relative to a serial CPU baseline.

The project was developed and evaluated on the **Bridges2 supercomputer**
as part of advanced high-performance computing coursework and is presented here as a
**standalone systems and GPU programming portfolio project** suitable for
research-oriented and performance-critical engineering roles.

---

## Overview

Particle simulations are a common workload in scientific computing, physics,
and engineering applications. As problem sizes grow, purely serial CPU
implementations become a performance bottleneck.

This project explores how a particle simulation can be **accelerated using CUDA** by:

- Parallelizing per-particle computations on the GPU
- Managing memory layout and access patterns efficiently
- Comparing performance against a serial CPU implementation
- Validating correctness using automated tools and reference outputs
- Running experiments on a production **supercomputing environment (Bridges2)**

The emphasis is on **performance-aware system design**, not merely functional correctness.

---

## What This Project Demonstrates

- CUDA kernel design and GPU parallelization strategies
- Serial CPU vs parallel GPU benchmarking
- Memory-access considerations in particle-based simulations
- Correctness verification using automated grading and reference outputs
- Execution on a production supercomputing environment (Bridges2 / SLURM)
- Practical performance analysis grounded in real measurements

---

## Repository Structure
```
.
├── particle_simulation.cu # CUDA implementation of particle simulation
├── serial.cu # Serial CPU baseline implementation
├── cuda_serial.cpp # CPU reference implementation
├── common.cu # Shared CUDA utilities
├── common.h # Shared headers
├── autograder.cu # Correctness verification tooling
├── Makefile # Build configuration
├── job-bridges-gpu # SLURM job script for GPU execution
├── job-bridges-serial # SLURM job script for serial execution
├── gen_gpusum.py # Helper scripts for analysis
├── report.pdf # Final report with methodology and results
└── README.md
```

---

## Build Instructions

### Local Build (CUDA-enabled environment)

Ensure that CUDA is properly installed and accessible.

```bash
make
This builds executables for both the serial CPU and CUDA GPU implementations.

Running the Simulation
Run Locally
./serial
./gpu
Run on Bridges2 (SLURM)
The project was executed on the Bridges2 supercomputer using batch job scripts.

Example usage:

sbatch job-bridges-serial
sbatch job-bridges-gpu
Refer to the provided job-bridges-* scripts for exact resource allocation
and execution details.
```
Performance Results (Summary)
The CUDA implementation achieves a clear performance improvement
over the serial CPU baseline for sufficiently large problem sizes.

Speedup increases with problem scale, consistent with GPU parallelism benefits.

Correctness was validated prior to benchmarking using automated tools.

Detailed methodology, plots, and analysis are provided in the final report.

📄 See report.pdf for full experimental details and performance analysis.

Correctness and Validation
Outputs were validated against reference implementations

Automated correctness checks were used to ensure numerical accuracy

Performance measurements were collected only after correctness was confirmed

Environment
Languages: CUDA C/C++, C++, Python

Build System: Make

Compute Platform: Bridges2 Supercomputer (GPU nodes)

Execution Model: Serial CPU vs CUDA GPU

Scheduler: SLURM

Notes on Scope
This project focuses on GPU acceleration and performance analysis.
It does not attempt to:

Claim production-level tuning beyond coursework scope

Generalize results to all particle simulation workloads

Present theoretical speedup without empirical validation

The goal is to demonstrate sound GPU programming practices,
performance reasoning, and system-level thinking.

Author
Jesus Gil

This project is part of a broader portfolio that includes:

Research-grade work in hybrid quantum machine learning

Applied machine learning systems

Frontend and full-stack system design

Blockchain-based security architectures
