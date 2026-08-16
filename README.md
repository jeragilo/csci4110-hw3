# CUDA-Accelerated Particle Simulation

A high-performance computing project that implements a particle simulation in **CUDA C/C++** and compares GPU execution with a serial CPU baseline.

The project was developed and evaluated on the **Bridges2 supercomputer** and focuses on practical GPU programming, correctness validation, SLURM-based execution, and performance analysis.

## Project Goals

The repository explores a central HPC question: how effectively can a particle-based workload be parallelized on a GPU relative to serial execution?

The implementation focuses on:

- parallelizing particle computations with CUDA kernels;
- comparing GPU and serial CPU implementations;
- reasoning about memory access and GPU execution behavior;
- validating numerical correctness before benchmarking;
- executing experiments through SLURM on Bridges2; and
- analyzing performance as workload size changes.

## Technology Stack

| Area | Technologies |
|---|---|
| GPU programming | CUDA C/C++ |
| CPU baseline | C/C++ |
| Build system | Make |
| HPC scheduler | SLURM |
| Compute environment | Bridges2 Supercomputer |
| Analysis utilities | Python |

## Repository Contents

The repository contains the actual CUDA implementation, serial/reference implementations, shared utilities, validation tooling, SLURM job scripts, and the original experimental report.

```text
cuda-particle-simulation-hpc/
├── gpu.cu
├── cuda_serial.cpp
├── common.cu
├── common.h
├── autograder.cu
├── Makefile
├── job-bridges-gpu
├── job-bridges-serial
├── auto-bridges-gpu
├── gen_gpusum.py
├── Homework 3_ Parallelizing a Particle Simulation REPORT (1).pdf
└── README.md
```

## Implementation

### GPU Version

`gpu.cu` contains the CUDA implementation of the particle simulation. Particle-level work is mapped onto GPU execution so that many particle computations can proceed in parallel.

### CPU / Reference Version

The repository includes CPU/reference code used to establish expected behavior and provide a comparison point for the GPU implementation.

### Correctness Validation

Correctness is treated separately from speed. The repository includes validation/autograding utilities so that output can be checked before interpreting timing results.

This distinction is important in performance engineering: an implementation is only meaningfully faster if it still produces valid results.

## Build

A CUDA-capable environment with `nvcc` is required.

```bash
make
```

The included `Makefile` defines the project build targets.

## Running on Bridges2

The repository includes separate SLURM job scripts for GPU and serial execution.

```bash
sbatch job-bridges-gpu
sbatch job-bridges-serial
```

These scripts capture the HPC execution workflow used for the project rather than presenting the code only as a local demonstration.

## Performance Interpretation

The experiments compare serial CPU and CUDA GPU execution and examine how the usefulness of GPU parallelism changes with problem scale.

The project report contains the detailed measurements and analysis. The main qualitative observation is that GPU acceleration becomes more useful as sufficient parallel work is available to offset GPU execution and data-management overhead.

I intentionally do not report a single universal speedup value here because performance depends on workload size and experimental configuration. The original report in this repository contains the measured results for the tested configurations.

## Skills Demonstrated

- CUDA kernel development
- C/C++ systems programming
- GPU parallelization
- CPU-vs-GPU benchmarking
- Performance reasoning
- Numerical correctness validation
- SLURM batch scheduling
- Supercomputing workflows
- Reproducible experimental reporting

## Scope and Limitations

This project originated in advanced HPC coursework and is presented as a focused GPU-programming and performance-analysis portfolio project.

It does not claim:

- production-level optimization for every GPU architecture;
- universal speedup across particle-simulation workloads; or
- that GPU execution is automatically advantageous at every problem size.

Instead, it demonstrates the engineering workflow of implementing, validating, executing, and analyzing a parallel scientific workload on real HPC infrastructure.

## Author

**Jesús Gil**  
Computer Science · Applied Mathematics · Quantum Computing · Machine Learning · HPC

[GitHub](https://github.com/jeragilo) · [LinkedIn](https://www.linkedin.com/in/jesusrgil)
