# **GPU‑LOKI Contribution Guide**

Thank you for your interest in contributing to **GPU‑LOKI**, a modern GPU‑accelerated reimagining of LLNL’s LOKI Vlasov‑Poisson / Vlasov‑Maxwell solver.  
This project is experimental, community‑driven, and open to contributors of all skill levels — from CUDA experts to documentation writers.

This guide explains how to get involved, how to contribute code, how to report issues, and how to collaborate effectively.

---

## **1. Project Philosophy**

GPU‑LOKI is built on three principles:

1. **Accessibility** — modern plasma simulation should run on consumer GPUs, not only supercomputers.  
2. **Transparency** — clear architecture, readable code, and open design discussions.  
3. **Collaboration** — no single person is expected to build the entire solver.  
   Contributions of any size are welcome.

If you want to help, you’re already part of the project.

---

## **2. Ways You Can Contribute**

You don’t need to write CUDA kernels to be valuable. Here are meaningful contribution paths:

### **Code Contributions**
- GPU kernels (CUDA/HIP/JAX)
- Poisson solver (FFT or iterative)
- Maxwell solver (FDTD/Yee)
- Multi‑GPU domain decomposition
- I/O layer (HDF5/Zarr)
- Python frontend (config parser, IC builder)
- Post‑processing tools

### **Non‑Code Contributions**
- Documentation
- Architecture diagrams
- Tutorials and examples
- Benchmarking and profiling
- Testing and validation
- Reviewing pull requests
- Creating issues and discussing design

### **Research Contributions**
- Numerical schemes (semi‑Lagrangian, finite‑volume)
- Stability analysis
- Mixed precision strategies
- GPU optimization techniques

If you’re unsure where to start, check the **Issues** tab — tasks are labeled by difficulty.

---

## **3. Getting Started**

### **Clone the repository**
```
git clone https://github.com/<yourname>/gpu-loki
cd gpu-loki
```

### **Install Python frontend**
GPU‑LOKI uses Python for configuration and post‑processing.

```
pip install -r requirements.txt
```

### **Build the CUDA core**
Instructions will vary by system, but typically:

```
mkdir build
cd build
cmake ..
make -j
```

If you don’t have a GPU environment set up, you can still contribute to Python tools, docs, and design.

---

## **4. Repository Structure**

```
gpu_loki/
│
├── core/              # CUDA/C++ solver
├── frontend/          # Python interface
├── io/                # HDF5/Zarr I/O
├── post/              # Analysis tools
└── docs/              # Architecture diagrams, notes
```

Each directory contains its own README describing internal structure.

---

## **5. Coding Standards**

### **General**
- Write clear, readable code.
- Prefer explicitness over cleverness.
- Document assumptions and numerical choices.

### **CUDA/C++**
- Use RAII and avoid raw pointers when possible.
- Keep kernels small and focused.
- Profile before optimizing.
- Use shared memory only when it improves performance measurably.

### **Python**
- Follow PEP8.
- Use type hints.
- Keep modules small and composable.

### **Commit Messages**
Use descriptive commit messages:

```
Add semi-Lagrangian kernel for vx/vy advection
Fix FFT-based Poisson solver boundary conditions
Improve Zarr chunking for 4D distribution storage
```

---

## **6. Pull Request Process**

1. Fork the repository.  
2. Create a feature branch:  
   ```
   git checkout -b feature/my-new-feature
   ```
3. Make your changes.  
4. Add tests if applicable.  
5. Submit a pull request.  
6. Participate in review discussions.  

Pull requests do **not** need to be perfect — maintainers will help refine them.

---

## **7. Issue Reporting**

If you encounter a bug or want to propose a feature:

- Open an issue.
- Provide a clear description.
- Include reproduction steps if relevant.
- Label the issue (bug, enhancement, question, design).

Good issues help everyone.

---

## **8. Design Discussions**

Large architectural changes should be discussed before implementation.  
You can:

- Open a “Design Proposal” issue  
- Share diagrams, pseudocode, or benchmarks  
- Ask for feedback from maintainers and contributors

GPU‑LOKI encourages open technical discussion.

---

## **9. Code of Conduct**

Be respectful, constructive, and collaborative.  
GPU‑LOKI welcomes contributors from all backgrounds and skill levels.

Harassment, discrimination, or hostility will not be tolerated.

---

## **10. A Note on Ambition**

GPU‑LOKI is a challenging project — but that’s the point.  
No single person is expected to rewrite LOKI alone.  
This repository exists to inspire collaboration, experimentation, and exploration.

If you contribute even a small piece, you’re helping build something that didn’t exist before.

---

## **11. Welcome to the Project**

Whether you’re here to write CUDA kernels, design numerical schemes, or improve documentation — thank you.

Your contributions matter.  
Your ideas matter.  
And your curiosity is exactly what this project was built for.
