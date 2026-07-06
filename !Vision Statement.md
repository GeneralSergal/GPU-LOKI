# **GPU‑LOKI Vision Statement**

**GPU‑LOKI** exists to bring high‑fidelity kinetic plasma simulation into the modern era of GPU computing.  
The project reimagines the original LLNL LOKI Vlasov solver — once bound to large MPI supercomputers — as an accessible, scalable, and GPU‑native research tool capable of running on hardware available to individual scientists, students, and independent developers.

Our vision is to create a **deterministic, high‑resolution Vlasov‑Poisson / Vlasov‑Maxwell solver** that leverages the massive parallelism of modern GPUs to explore plasma physics with clarity and precision that particle‑based methods cannot provide.  
We aim to make phase‑space simulation practical, fast, and open to everyone.

GPU‑LOKI is built on four core principles:

### **1. Accessibility**
Kinetic plasma simulation should not require institutional supercomputers.  
A single consumer GPU should be able to run meaningful Vlasov problems with modern numerical methods and mixed‑precision acceleration.

### **2. Transparency**
The architecture, algorithms, and data structures should be clear, documented, and understandable.  
Researchers should be able to inspect, modify, and extend the solver without navigating legacy HPC complexity.

### **3. Modernization**
GPU‑LOKI embraces contemporary computing tools — CUDA, NCCL, cuFFT, Zarr/HDF5, Python frontends, and multi‑GPU scaling — to deliver performance and usability far beyond the original LOKI design.

### **4. Collaboration**
GPU‑LOKI is not a one‑person rewrite.  
It is a community‑driven initiative where contributors of all backgrounds — CUDA developers, physicists, numerical analysts, Python engineers, and documentation writers — can help shape a next‑generation Vlasov solver.

---

## **Our Long‑Term Goal**

To build a fully GPU‑accelerated, multi‑GPU Vlasov‑Maxwell code that is:

- deterministic  
- high‑resolution  
- open‑source  
- reproducible  
- scientifically rigorous  
- and capable of exploring kinetic plasma phenomena with unprecedented clarity.

We want GPU‑LOKI to become a **reference implementation** for modern Eulerian plasma simulation — a tool that complements PIC codes like WarpX by offering noise‑free, phase‑space‑resolved kinetic physics.

---

## **Why This Matters**

The Vlasov equation describes plasma behavior at a level of detail unmatched by particle methods.  
Yet Vlasov solvers have historically been too computationally expensive for widespread use.

Modern GPUs change that.

GPU‑LOKI aims to demonstrate that **high‑fidelity kinetic simulation is no longer reserved for supercomputers** — it can be done on a single GPU, scaled across many, and shared openly with the world.

---

## **The Invitation**

GPU‑LOKI is a beginning, not a finished product.  
It is a blueprint, a challenge, and an opportunity for anyone who believes that scientific computing should be open, modern, and accessible.

Whether you contribute code, ideas, documentation, or testing — you help shape the future of kinetic plasma simulation.

Welcome to GPU‑LOKI.
