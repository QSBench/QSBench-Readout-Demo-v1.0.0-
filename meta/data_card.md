
Release overview

Dataset name: QSBench-Readout-Demo-v1.0.0
Release version: 1.1.0
Benchmark focus: readout-error robustness benchmark
Total rows: 2048
Shards: 4
Storage format: Parquet shards
Backend device: GPU
GPU requested: True
GPU available: True

What is inside this release?
This release is a synthetic quantum benchmark dataset for:

- expectation value regression
- circuit family classification
- noise robustness analysis
- circuit structure and complexity analysis
- hybrid quantum-classical experimentation

Generation profile

Qubits: 8
Depth: 6
Circuit family request: mixed
Circuit family: mixed (randomly sampled from the supported family pool).
Entanglement: full
Noise model: readout error (p0=0.02, p1=0.015).
Shots: 1024
Observable bases: Z, X, Y
Observable mode: mixed (global + per-qubit).
Approximate label heads: 27

Why this release is useful
This dataset is designed for:

- supervised learning on ideal and noisy expectation values
- benchmarking models across multiple circuit families
- robustness testing under configurable noise settings
- circuit-structure analysis using gate and connectivity metrics
- reproducible train/validation/test splits

Split policy

Train: 0.8
Validation: 0.1
Test: 0.1
Split distribution: train: 1640, val: 201, test: 207

Summary statistics
Rows: 2048 | Columns: 9 | Unique circuits: 2048 | Split summary: {'train': 1640, 'test': 207, 'val': 201}

Family coverage
hea: 390, random: 378, qft: 434, real_amplitudes: 405, efficient: 441

Files in the release

- meta.json
- schema.json
- coverage.json
- manifest.json
- report.json
- data_card.md
- CHANGELOG.md
- generation_log.json

Important notes

- split is assigned deterministically from circuit_hash.
- ideal_expval_* values come from clean simulation.
- noisy_expval_* values come from the selected noise model.
- error_* is the difference between ideal and noisy expectation values.
- The exact column layout is described in schema.json.
- The exact shard inventory is described in manifest.json.

Loading guidance

Use the Parquet shards for production workflows. CSV copies, when enabled, are provided for portability and quick inspection.
