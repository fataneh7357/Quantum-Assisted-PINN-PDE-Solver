# Explainable-QAPINN

**Explainable Quantum-Assisted Physics-Informed Neural Networks (QAPINNs)**

This project investigates how introducing a **variational quantum layer** changes the learning dynamics of Physics-Informed Neural Networks (PINNs).

The goal is **not to claim universal quantum advantage**, but to understand **when, why, and how** a quantum layer affects accuracy, optimization, parameter efficiency, computational cost, and generalization.

## PDE Benchmarks

We study two PDEs:

* **Allen–Cahn equation** — nonlinear reaction-diffusion problem
* **Heat equation** — linear diffusion problem

Classical PINNs are compared with hybrid **QAPINNs** using different numbers of qubits and quantum circuit layers.

## Quantum Architecture

The QAPINN combines:

**Classical encoder → Variational quantum circuit → Classical decoder**

The quantum circuit uses:

* Data re-uploading
* Parameterized $R_Y$ and $R_Z$ rotations
* CNOT-based ring entanglement
* Pauli-$Z$ expectation-value measurements

## Experiments

We investigate the effects of:

* Number of qubits
* Quantum circuit depth
* Parameter count
* PDE residual error
* Relative $L_2$ error
* Training time
* Memory requirements
* Temporal extrapolation
* Gradient and learning dynamics

## Repository Contents

```text
Explainable-QAPINN/
├── notebooks/       # PINN and QAPINN experiments
├── results/         # Experimental results and figures
├── report/          # Technical report
├── Key Findings/    # Key Findings
├── Future Works/    # Future Works
├── presentation/    # Project presentation
├── src/             # Reusable source code
├── requirements.txt
├── LICENSE
└── README.md
```

## Team

**[Your Name]** — Allen–Cahn equation and QAPINN analysis
**[Teammate Name]** — Heat equation and QAPINN analysis

## Objective

The central research question is:

> **How does the introduction of a variational quantum layer change the learning process of a Physics-Informed Neural Network?**

The results are used to identify the **benefits, limitations, and problem-dependent design principles** of QAPINNs.
