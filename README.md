# Explainable-QAPINN

**Explainable Quantum-Assisted Physics-Informed Neural Networks (QAPINNs): Investigating the Effect of Variational Quantum Layers on PINN Learning Dynamics**

This repository contains the source code, experimental results, figures, and documentation for our investigation of how introducing a variational quantum layer changes the learning behavior of Physics-Informed Neural Networks (PINNs).

The project focuses on **explainability rather than claiming universal quantum advantage**. We investigate when, why, and how a quantum layer modifies optimization, accuracy, parameter efficiency, computational cost, and generalization in physics-informed PDE solvers.

---

## Project Objectives

The main objectives are to:

* Compare classical PINNs with hybrid quantum-classical QAPINNs.
* Investigate the effect of the number of qubits on learning behavior.
* Investigate the effect of quantum circuit depth.
* Analyze the influence of data re-uploading and entanglement.
* Compare PDE residual and solution accuracy.
* Study parameter reduction introduced by quantum layers.
* Analyze training-time and computational overhead.
* Examine gradient dynamics and trainability.
* Evaluate generalization on unseen temporal domains.
* Develop a problem-specific methodology for designing QAPINN architectures and quantum circuits.

---

## PDE Benchmarks

Two partial differential equations are investigated.

### 1. Allen-Cahn Equation

The Allen-Cahn equation is used as the primary nonlinear benchmark because it contains nonlinear reaction dynamics and can exhibit sharp spatial structures.

The general form considered is

[
u_t = \epsilon^2 u_{xx} + f(u),
]

with appropriate initial and boundary conditions.

The Allen-Cahn experiments investigate multiple quantum configurations:

* 2 qubits with 1, 2, and 3 layers
* 4 qubits with 1, 2, and 3 layers
* 6 qubits with 1 and 2 layers
* Classical PINN baseline

### 2. Heat Equation

The Heat equation is used as a linear diffusion benchmark:

[
u_t = \alpha u_{xx}.
]

The experiments investigate:

* Classical PINN
* 2 qubits with 1 layer
* 2 qubits with 3 layers
* 4 qubits with 1 layer
* 4 qubits with 3 layers

Additional configurations can be added as computational resources permit.

---

## QAPINN Architecture

The QAPINN consists of three components:

[
(x,t)
\rightarrow
\text{Classical Encoder}
\rightarrow
\text{Variational Quantum Circuit}
\rightarrow
\text{Classical Decoder}
\rightarrow
u(x,t).
]

The quantum layer receives continuous features produced by the classical encoder and returns expectation-value features to the classical decoder.

The quantum circuit uses:

* Data re-uploading
* Parameterized (RY) and (RZ) rotations
* CNOT-based entanglement
* Ring/periodic entanglement topology
* Pauli-(Z) expectation-value measurements

The number of quantum trainable parameters scales as

[
P_{\mathrm{quantum}}
====================

2LN_q,
]

where (L) is the number of quantum layers and (N_q) is the number of qubits.

---

## Experimental Metrics

The following metrics are used to compare the models:

### Accuracy

* Relative (L_2) error
* PDE residual MSE
* PDE residual RMSE

### Computational cost

* Training time
* Number of trainable parameters
* Model memory
* Peak training memory

### Generalization

* Temporal extrapolation error on (t>1)

### Learning dynamics

* Total loss
* PDE loss
* Initial-condition loss
* Boundary-condition loss
* Gradient magnitude
* Quantum-gradient behavior
* Classical-gradient behavior

These metrics allow us to investigate not only which model performs better, but also how the quantum layer changes the learning process.

---

## Main Research Questions

The experiments address the following questions:

### Q1. When does a quantum layer improve PINN learning?

We examine how accuracy and PDE satisfaction change as the number of qubits and circuit layers are varied.

### Q2. Why does circuit depth affect performance?

Increasing circuit depth increases expressivity and the number of trainable quantum parameters, but can also increase optimization difficulty and computational cost.

### Q3. How does the number of qubits affect the model?

Increasing the number of qubits changes both the dimension of the quantum feature space and the number of quantum parameters.

### Q4. What is gained by introducing a quantum layer?

Potential benefits include:

* Reduced total parameter count
* Nonlinear quantum feature transformations
* Increased representational flexibility
* Alternative feature mappings through quantum expectation values

### Q5. What is lost?

The experiments also investigate:

* Increased training time
* Quantum simulation overhead
* Sensitivity to circuit depth
* Possible optimization difficulties
* Generalization degradation in some configurations

---

## Repository Structure

```text
Explainable-QAPINN/
│
├── README.md
│
├── report/
│   └── QAPINN_Report.pdf
│
├── presentation/
│   └── QAPINN_Slides.pdf
│
├── notebooks/
│   ├── Allen_Cahn_PINN.ipynb
│   ├── Allen_Cahn_QAPINN.ipynb
│   ├── Heat_PINN.ipynb
│   └── Heat_QAPINN.ipynb
│
├── src/
│   ├── pinn.py
│   ├── qapinn.py
│   ├── quantum_circuit.py
│   ├── training.py
│   └── evaluation.py
│
├── results/
│   ├── tables/
│   ├── figures/
│   └── logs/
│
├── requirements.txt
│
└── LICENSE
```

---

## Software

The experiments use Python and scientific machine-learning libraries including:

* Python
* PyTorch
* NumPy
* SciPy
* Matplotlib
* Pandas
* PennyLane

The quantum circuits are evaluated using a simulator rather than physical quantum hardware.

---

## Reproducibility

The experiments use fixed random seeds where applicable.

The repository will provide:

1. Jupyter notebooks containing the experiments.
2. Model and circuit configurations.
3. Training parameters.
4. Evaluation procedures.
5. Experimental results.
6. Figures used in the technical report.
7. Software dependency information.

To reproduce an experiment, install the required packages and execute the corresponding notebook.

---

## Results

The experiments demonstrate that the effect of a quantum layer is **problem- and architecture-dependent**.

For the Allen-Cahn equation, the experiments show that increasing the number of qubits or circuit layers does not necessarily produce monotonic improvement. Certain shallow quantum configurations achieve competitive accuracy with substantially fewer trainable parameters, while deeper configurations can introduce optimization and computational penalties.

For the Heat equation, the results similarly demonstrate a trade-off between parameter reduction, solution accuracy, training time, and temporal extrapolation.

Therefore, the central conclusion of this project is not that QAPINNs universally outperform classical PINNs. Instead, the results indicate that **quantum-layer design is an important determinant of QAPINN learning behavior**.

---

## Research Focus

The project investigates the following relationship:

[
\boxed{
\text{Quantum Circuit Design}
\rightarrow
\text{Learning Dynamics}
\rightarrow
\text{PDE Accuracy}
}
]

with particular emphasis on:

[
N_q,\quad
L,\quad
\text{encoding},\quad
\text{entanglement},\quad
\text{measurement},\quad
\text{gradient dynamics}.
]

---

## Documentation

* **Technical Report:** `report/QAPINN_Report.pdf`
* **Presentation:** `presentation/QAPINN_Slides.pdf`
* **Experiments:** `notebooks/`
* **Results:** `results/`

---

## Team

This project was developed as a collaborative investigation of explainable quantum-enhanced physics-informed neural networks.

---

## License

This project is intended for research and educational purposes.
