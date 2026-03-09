<h1> ML4Sci Test Tasks - QMLHEP 2026 </h1>

## Overview

This repository contains my implementations and documentation for the **ML4Sci GSoC 2026** application test tasks, focusing on **Quantum Machine Learning for High Energy Physics (QMLHEP)**.


### [`tasks-i-ii-iii-QMLHEP/`](tasks-i-ii-iii-QMLHEP/)

**Quantum Circuit Implementation & Research Exploration**

- **Task I:** Quantum Computing Part : [`tasks_i_ii.ipynb`](tasks-i-ii-iii-QMLHEP/tasks_i_ii.ipynb)
  
- **Task II:** Graph Neural Network (GNN) : [`tasks_i_ii.ipynb`](tasks-i-ii-iii-QMLHEP/tasks_i_ii.ipynb)
  
- **Task III:** Open task : [`task-iii.md`](tasks-i-ii-iii-QMLHEP/task-iii.md)

---

### [`task-ix-QMLHEP/`](task-ix-QMLHEP/)

**Classical and Quantum KAN Architectures**

Implementation and comparison of **Kolmogorov-Arnold Network (KAN)** architectures for MNIST digit classification.

#### Models Implemented:

1. **KAN v0 (Spline-Based KAN)** - Architecture with B-spline basis functions
2. **KAN v1 (Hybrid Linear + Spline KAN)** - Improved stability with dual representation
3. **KAN v2 (Chebyshev Polynomial KAN)** - Efficient polynomial basis approach
4. **ConvChebyKAN** - Convolutional architecture with KAN layers

#### Performance Highlights:

| Model | Parameters (M) | Test Accuracy | Key Feature |
|-------|----------------|---------------|-------------|
| KAN v0 | 0.419 | 94.99% | Pure KAN concept |
| KAN v1 | 1.202 | 97.56% | Hybrid representation |
| KAN v2 | 0.263 | 97.19% | Lowest compute cost |
| **ConvChebyKAN** | **0.529** | **98.63%** | **Highest accuracy** |

- [`task_ix_classical_KAN.ipynb`](task-ix-QMLHEP/task_ix_classical_KAN.ipynb) - Implementation notebook
- [`task-ix-quantum-extended-design.png`](task-ix-QMLHEP/task-ix-quantum-extended-design.png) - Quantum extension design
- [`README.md`](task-ix-QMLHEP/README.md) - Detailed model documentation
- Performance visualization plots
    - [`task-ix-QMLHEP\model_ConvKAN_accuracy_and_loss_plots.png`](task-ix-QMLHEP\model_ConvKAN_accuracy_and_loss_plots.png)
    - [`task-ix-QMLHEP\model0_vs_model1_vs_model2_testAccuracyComparison.png.png`](task-ix-QMLHEP\model0_vs_model1_vs_model2_testAccuracyComparison.png.png)
    - [`task-ix-QMLHEP\model0_vs_model1_vs_model2_testLossComparison.png`](task-ix-QMLHEP\model0_vs_model1_vs_model2_testLossComparison.png)
