---
license: cc-by-nc-4.0
task_categories:
- tabular-regression
- feature-extraction
language:
- en
tags:
- qiskit
- quantum-circuits
- synthetic-dataset
- benchmark
- expectation-values
- quantum-computing
- qml-benchmark
- quantum dataset
- qml dataset
- quantum benchmark
- noisy quantum data
- readout error
- measurement noise
- asymmetric noise
- error mitigation
- noise robustness
pretty_name: QSBench Readout Error Demo v1.0.0 – Measurement Noise Dataset (n=8)
size_categories:
- 1K<n<10K
---
![QSBench Logo](https://i.imgur.com/VyLgYtf.png)

🌐 [Website](https://qsbench.github.io) | 🤗 [Dataset](https://huggingface.co/datasets/QSBench/QSBench-Readout-Demo-v1.0.0) | 🛠️ [GitHub](https://github.com/QSBench/QSBench-Readout-Demo-v1.0.0) | 🚀 [Interactive Demo](https://huggingface.co/QSBench/spaces)

# QSBench Readout Error Demo v1.0.0

**Measurement noise dataset** — focuses on readout (measurement) errors, one of the most critical and impactful noise sources in quantum expectation value estimation.

This demo uses the dedicated `readout` noise model with asymmetric flip probabilities (`p0` and `p1`).

**2048 high-quality synthetic quantum circuits with realistic readout errors.**

Designed for researchers and engineers working on readout error mitigation, accurate expectation value prediction, and noise-aware quantum machine learning.

### Why this dataset?
Readout errors often dominate the total error budget in quantum computations. Unlike symmetric depolarizing noise, readout errors are **asymmetric** (different probability of flipping 0→1 and 1→0).  
This dataset allows you to:

- Train and evaluate **readout error mitigation** techniques
- Study how measurement noise distorts different observables (Z, X, Y)
- Benchmark robustness of QML models to realistic measurement errors
- Compare the impact of readout noise versus relaxation noise

### Use Cases
- Readout error mitigation research
- Accurate expectation value prediction under measurement noise
- Benchmarking noise robustness of quantum classifiers and regressors
- Feature engineering for measurement-aware quantum ML
- Comparing different error mitigation strategies

### Dataset Overview
- **Samples**: 2048
- **Qubits**: 8
- **Depth**: 6
- **Circuit Families**: Mixed (HEA, RealAmplitudes, QFT, Efficient SU(2), Random)
- **Entanglement**: Full
- **Noise**: Readout Error (`p0 = 0.02`, `p1 = 0.015`)
- **Observables**: Z, X, Y in mixed mode (global + per-qubit)
- **Shots**: 1024
- **Splits**: Train / Validation / Test — deterministic hash-based

### What's Inside Each Sample
Each sample in the Parquet files contains:
- Raw and transpiled QASM representations
- Circuit adjacency matrix
- Gate statistics (CX, H, RX, RY, RZ, etc.)
- Structural metrics: Gate entropy + Meyer-Wallach entanglement
- **Ideal expectation values**
- **Noisy expectation values** (after readout errors)
- **Explicit error targets**: `error_<label> = ideal - noisy`
- Circuit metadata and generation parameters
- Deterministic split label

### Key Learning Signals
For every observable, the dataset provides: `ideal_expval_*`, `noisy_expval_*`, `error_*`, `sign_ideal_*`, `sign_noisy_*`.  
This enables both regression tasks and binary classification of sign flips caused by measurement errors.

### QSBench-Readout: Asymmetric Measurement Noise
**You don't need a PhD in Quantum Physics to use this dataset.**  
This dataset represents the real-world measurement imperfections you encounter when running circuits on actual quantum hardware.

### The ML Mission: Complex Tabular Regression
Your goal is to build models that can understand and compensate for asymmetric readout errors, which behave differently depending on the prepared quantum state.

### Dataset Anatomy (Features & Targets)

| Group            | Column Name                        | What is it for ML? |
|------------------|------------------------------------|--------------------|
| **Features (X)** | `adjacency`                        | Circuit connectivity |
| **Features (X)** | `qasm_transpiled`                  | Hardware-specific circuit representation |
| **Features (X)** | `single_qubit_gates`, `two_qubit_gates` | Gate counts |
| **Target (y)**   | `error_Z_global`, `error_X_global` | Continuous regression targets (measurement error) |
| **Physics**      | `meyer_wallach`                    | Entanglement level |

### Quick Start Idea
Investigate whether highly entangled states suffer more from readout errors or if the effect is mostly state-independent.

### Load the Dataset
```python
from datasets import load_dataset
# Load the readout error demo dataset
dataset = load_dataset("QSBench/QSBench-Readout-Demo-v1.0.0", split="train")
print(dataset[0])
```

### Related QSBench Datasets

- [QSBench-Thermal-Demo-v1.0.0](https://huggingface.co/datasets/QSBench/QSBench-Thermal-Demo-v1.0.0)

- [QSBench-Device-Demo-v1.0.0](https://huggingface.co/datasets/QSBench/QSBench-Device-Demo-v1.0.0)

- [QSBench-Amplitude-v1.0.0-demo](https://huggingface.co/datasets/QSBench/QSBench-Amplitude-v1.0.0-demo)

- [QSBench-Depolarizing-Demo-v1.0.0](https://huggingface.co/datasets/QSBench/QSBench-Depolarizing-Demo-v1.0.0)

### Part of the QSBench Family

his is a small public **demo version**. Full-scale Readout Noise Pack and other specialized releases are available on the [QSBench website](https://qsbench.github.io).

### Notes

- Fully synthetic dataset generated with Qiskit Aer
  
- No real-world or personal data

- **License:** CC BY-NC 4.0 (Personal & Research Use)

**Questions or custom requests?** Visit QSBench [website](https://qsbench.github.io) or open an issue on [GitHub](https://github.com/QSBench/QSBench-Readout-Demo-v1.0.0/issues).

---
*Generated with QSBench Generator v5.1.0*