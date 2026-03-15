# Quantum Kolmogorov–Arnold Network (QKAN)

Suggested architecture

![task-ix-quantum-extended-design.png](task-ix-quantum-extended-design.png)
[task-ix-quantum-extended-design.png](task-ix-quantum-extended-design.png)


## Overview

This project proposes a **Quantum Kolmogorov–Arnold Network (QKAN)** designed for machine learning tasks in **High Energy Physics (HEP)**. The architecture builds on **Kolmogorov–Arnold Networks (KAN)** and their quantum extension **QKAN**, while addressing several practical limitations of the original QKAN framework.

The goal is to create a **practical and trainable QKAN architecture** using quantum machine learning tools such as **PennyLane**, and evaluate its performance on physics datasets relevant to experiments at the **Large Hadron Collider (LHC)**.


## Background

### Kolmogorov–Arnold Networks (KAN)

KANs are neural architectures inspired by the **Kolmogorov–Arnold representation theorem**, where a multivariate function can be represented as a composition of univariate functions and summations.

Instead of fixed activation functions at nodes, KAN places **learnable functions on edges**:

$$
y_j = \sum_{i=1}^{n} \phi_{ij}(x_i)
$$

Each edge function ( \phi_{ij} ) is a learnable **univariate nonlinear transformation**.


### Quantum Kolmogorov–Arnold Networks (QKAN)

QKAN extends KAN to the quantum setting by representing edge functions as **polynomial transformations** implemented within quantum circuits. These transformations rely on quantum linear algebra tools such as:

* Block encoding
* Quantum Singular Value Transformation (QSVT)
* Chebyshev polynomial expansions

These methods allow nonlinear activation functions to be implemented while maintaining **unitary quantum operations**.


## Limitations of Existing QKAN Approaches

Although theoretically powerful, the current QKAN framework faces several practical limitations:

### 1. Large Block-Encoding Overhead

Representing vectors and matrices using **block encoding** often requires additional **ancilla qubits** and controlled operations.
For realistic datasets, this leads to significant circuit width and resource overhead.

### 2. Deep QSVT Circuits

Implementing polynomial transformations through **Quantum Singular Value Transformation (QSVT)** requires long sequences of controlled unitary operations, resulting in **deep quantum circuits**.

### 3. Poor NISQ Compatibility

The depth and resource requirements of full QSVT pipelines make the architecture difficult to execute on **Noisy Intermediate-Scale Quantum (NISQ)** devices.

### 4. Expensive Polynomial Evaluation

Activation functions represented through high-degree Chebyshev expansions can require many controlled transformations, increasing training complexity.


## Proposed QKAN Architecture

To address these issues, I propose a **classical–quantum architecture** where quantum circuits approximate the **KAN edge functions**, while classical layers handle preprocessing and aggregation.

### Architecture Pipeline

```
Input Features
      │
      ▼
Classical Feature Compression
(Linear / MLP layer)
      │
      ▼
KAN Edge Functions
(each edge implemented by a PQC)
      │
      ▼
Quantum Circuit Evaluation
(expectation values)
      │
      ▼
KAN Summation Layer
      │
      ▼
Output Layer
```


## Quantum Edge Functions

Each KAN edge function ( \phi(x) ) is implemented using a **Parameterized Quantum Circuit (PQC)**.

Example circuit structure:

```
AngleEmbedding(x)
      ↓
Parameterized rotation layers
      ↓
Entangling gates
      ↓
Expectation measurement
```

The measured expectation value acts as the **nonlinear transformation** applied to the input feature.

This allows the model to learn flexible nonlinear functions without requiring explicit polynomial transformations via QSVT.


## Advantages of the Approach

The proposed design improves practicality while maintaining the KAN structure:

* **Reduced circuit depth**
  PQCs approximate nonlinear functions without requiring deep QSVT pipelines.

* **Lower quantum resource requirements**
  Classical preprocessing reduces the number of qubits needed for quantum circuits.

* **Better NISQ compatibility**
  Shallow PQC circuits are more suitable for near-term quantum hardware.

* **Simpler training pipeline**
  The architecture integrates naturally with **PennyLane and PyTorch**.

* **Preserves KAN structure**
  Edge-based nonlinear functions and summation layers remain intact.



## Goal

The goal of this work is to:

* Implement the **QKAN architecture**
* Study its expressivity compared to classical KAN models
* Benchmark performance on **HEP datasets**
* Investigate whether **quantum edge functions** provide advantages in physics-inspired machine learning tasks.