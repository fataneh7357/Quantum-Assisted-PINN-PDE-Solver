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
├── Report/          # Technical report
├── Key Findings/    # Key Findings
├── Future Works/    # Future Works
├── presentation/    # Project presentation
├── Requirements
├── LICENSE
└── README.md
```
## Reproducibility

To reproduce the experiments:

1. Clone the repository.
2. Install the required Python packages listed requirements.txt .
3. Open the corresponding notebooks.
4. Run the cells in order.
5. Use the same model configurations, random seeds, training epochs, and PDE parameters specified in each notebook.
6. The experiments use the PennyLane `default.qubit` simulator and do not require quantum hardware.

All reported results, figures, and configurations are shown at the end of each notebook.

### Computational Reproducibility Note

The 6-qubit Allen–Cahn experiments were computationally intensive and resulted in an out-of-memory (OOM) failure in the cloud runtime. Because the experiment was executed in an ephemeral environment, the runtime was restarted and the unmounted checkpoint directory was lost along with the intermediate training state. Consequently, the original 6-qubit run could not be resumed from a checkpoint. Numerical results that had already been recorded before the failure were retained and used for the reported analysis and figures.



## Team

**[Fataneh Bakherad]** — Allen–Cahn equation and QAPINN analysis
**[Mehrdad Ghanbari Mobarakeh]** — Heat equation and QAPINN analysis

## Objective

The central research question is:

> **How does the introduction of a variational quantum layer change the learning process of a Physics-Informed Neural Network?**

The results are used to identify the **benefits, limitations, and problem-dependent design principles** of QAPINNs.
