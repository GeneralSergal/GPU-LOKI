# **GPU‑LOKI — A Modern GPU‑Accelerated Reimagining of LLNL’s LOKI Vlasov Solver**

**GPU‑LOKI** is an experimental initiative to modernize and re‑architect the classic LLNL plasma simulation code **LOKI** — originally designed for large MPI‑based supercomputers — into a fully GPU‑accelerated solver capable of running on modern consumer and datacenter GPUs.

The original LOKI (Vlasov‑Poisson / Vlasov‑Maxwell solver) was built for LLNL’s TOSS2/TOSS3 HPC systems using PETSc, ParMETIS, SuperLU, MPI, and distributed HDF5.  
Today, GPUs such as the RTX 3090/4090, A100, H100, and MI300 can outperform entire older clusters thanks to massive parallelism, tensor cores, mixed precision, and terabytes‑per‑second memory bandwidth.

This repository is **not** a rewrite of LOKI.  
It is a **starting point**, a **design draft**, and a **collaboration seed** for anyone interested in building a modern GPU‑based Vlasov solver inspired by LOKI’s physics and structure.

---

# **✨ Project Goals**

- Develop a **GPU‑native architecture** for Vlasov‑Poisson and Vlasov‑Maxwell systems.  
- Implement the 4D distribution function  
  \[
  f(x, y, v_x, v_y)
  \]  
  using CUDA‑optimized memory layouts.
- Replace PETSc/SuperLU with **cuFFT, cuSPARSE, and custom GPU solvers**.
- Provide a **Python frontend** for configuration, initial conditions, and analysis.
- Support **mixed precision** (FP32/FP16/BF16) for performance.
- Enable **multi‑GPU scaling** via NCCL or CUDA‑aware MPI.
- Make the project approachable for contributors.

---

# **🧩 Architecture Overview**

## **1. Frontend (Python)**  
- YAML/TOML configuration files  
- Initial condition generator (Maxwellian, Landau damping, noisy Maxwellian, external 2D)  
- Run controller  
- Post‑processing tools (NumPy, JAX, Matplotlib)

## **2. Core Solver (CUDA/C++)**

### **2.1 Data Structures**
- 4D distribution arrays: `f[ix][iy][ivx][ivy]`  
- Electric and magnetic fields on a 2D grid  
- Diagnostics: energy, fluxes, probe data

### **2.2 Time Integration**
- RK4 / RK6 temporal schemes  
- Semi‑Lagrangian or high‑order finite‑volume advection  
- Mixed precision compute paths  
- CUDA kernels:
  - Configuration‑space advection  
  - Velocity‑space advection  
  - Poisson solver (FFT‑based or iterative)  
  - Maxwell solver (FDTD/Yee)  
  - Reductions and diagnostics

## **3. Multi‑GPU Layer**
- Domain decomposition in (x, y)  
- Full velocity space per GPU  
- Halo exchange via NCCL or CUDA‑aware MPI  
- Overlap communication with computation

## **4. I/O System**
- HDF5 or Zarr for large 4D datasets  
- Chunked GPU‑friendly storage  
- Checkpoints for restart  
- 2D field snapshots and 0D time histories

## **5. Post‑Processing**
- Python analysis tools  
- Visualization of fields, slices, spectra, damping rates  
- Energy and flux diagnostics

---

# **📦 Suggested Repository Structure**

```
gpu_loki/
│
├── core/              # CUDA/C++ solver
│   ├── cuda_kernels.cu
│   ├── solver.hpp
│   ├── grid.hpp
│   └── species.hpp
│
├── frontend/          # Python interface
│   ├── config_parser.py
│   ├── run.py
│   └── ic_builder.py
│
├── io/                # HDF5/Zarr I/O
│   ├── hdf5_io.cpp
│   └── zarr_io.cpp
│
├── post/              # Analysis tools
│   ├── analysis.py
│   └── plotting.py
│
└── docs/              # Architecture diagrams, notes
```

---

# **🚀 Minimal Working Prototype (MVP)**

The first milestone is intentionally small:

- 2D/2V Vlasov–Poisson  
- Semi‑Lagrangian advection  
- FFT‑based Poisson solver (cuFFT)  
- Single species  
- Single GPU  
- Grid size: **256 × 256 × 128 × 128** (fits comfortably on RTX 3090)  
- FP32 with optional FP16/BF16 paths  

Once this works, the project can expand to full 4D, multi‑GPU, and Maxwell support.

---

# **🛠 Roadmap**

### **Stage 1 — Minimal GPU Prototype**
- Basic CUDA kernels  
- Poisson solver  
- Python frontend

### **Stage 2 — Full 4D Vlasov–Poisson**
- Memory optimization  
- Mixed precision  
- Performance tuning

### **Stage 3 — Multi‑GPU Scaling**
- NCCL / MPI  
- Domain decomposition  
- Halo exchange

### **Stage 4 — Maxwell Solver**
- FDTD  
- GPU curl operations  
- EM wave propagation

### **Stage 5 — I/O + Post‑Processing**
- HDF5/Zarr  
- Python analysis suite  
- Visualization tools

---

# **🤝 Contributing**

GPU‑LOKI is open to anyone interested in:

- CUDA programming  
- GPU optimization  
- Plasma physics  
- Numerical methods  
- Python tooling  
- Documentation  
- Testing and validation  

If you want to help, feel free to open an issue, discuss ideas, or submit a pull request.

---

# **🐺 Why GPU‑LOKI?**

Because the original LOKI is powerful but tied to an older HPC era.  
Modern GPUs can run the same physics faster, cheaper, and more accessibly.  
And because — let’s be honest — the idea that **Loki rewrites LOKI** is too good not to exist.
