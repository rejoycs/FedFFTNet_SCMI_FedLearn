# 📸 Source Camera Model Identification via Federated Learning using Laplacian-based Patches

<div align="center">

![Python](https://img.shields.io/badge/Python-3.9+-blue?style=for-the-badge&logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-ee4c2c?style=for-the-badge&logo=pytorch)
![Federated Learning](https://img.shields.io/badge/Federated-Learning-green?style=for-the-badge)
![IEEE TAI](https://img.shields.io/badge/IEEE-TAI-orange?style=for-the-badge)
<!-- ![Research](https://img.shields.io/badge/Research-Academic-purple?style=for-the-badge)
![License](https://img.shields.io/badge/License-Academic-lightgrey?style=for-the-badge) -->

</div>

---

## 📖 Overview

Official implementation of the paper:

> **"Source Camera Model Identification via Federated Learning using Laplacian-based Patches"**  
> Published in **IEEE Transactions on Artificial Intelligence (IEEE TAI)**.

This work proposes a **Federated Learning (FL)** based framework for **Source Camera Model Identification (SCMI)** using **Laplacian-based image patches** and the proposed **FedFFTNet** architecture.

The framework consists of:

- 📌 Laplacian-based informative patch extraction
- 🌐 Federated data distribution across clients
- 🧠 Federated model training using FedFFTNet
- 📷 Source Camera Model Identification

---

## 🔗 Paper

📄 **Paper Link:**  
[Source Camera Model Identification via Federated Learning using Laplacian-based Patches](https://ieeexplore.ieee.org/abstract/document/11229953)

---

# 📂 Repository Workflow

The complete pipeline consists of two major stages:

```text
Raw Images
    │
    ▼
Laplacian-based Patch Extraction
    │
    ▼
Federated Client Distribution
    │
    ▼
FedFFTNet Training
    │
    ▼
Source Camera Model Prediction
```

---

# 📁 Dataset Structure

Ensure your dataset is pre-split into `train` and `test` folders.

```text
data/
├── train/
│   ├── class_1/
│   ├── class_2/
│   └── ...
│
├── test/
│   ├── class_1/
│   ├── class_2/
│   └── ...
```

---

# 🧩 Step 1 — Laplacian-based Image Patching

Notebook:

```text
Fed_DataSplit_Laplacian.ipynb
```

This notebook performs:

- Laplacian-based informative patch extraction
- Federated client data distribution
- Global server data allocation
- Test set generation

---

## ⚙️ Hyperparameters

| Variable | Type | Default | Description |
|---|---|---|---|
| `datapath` | `str` | `./data` | Source dataset directory |
| `number_clients` | `int` | `5` | Number of federated clients |
| `initial_ratio` | `float` | `0.06` | Ratio of globally available data |
| `dist_type` | `str` | `equal` | Data distribution type (`equal`, `random`, `skew`) |

---

## 🖼️ Patching Pipeline

<div align="center">

<img src="images/patching_method.png" alt="Patching Method" width="450"/>

</div>

<p align="center">
<b>Figure 1.</b> Laplacian-based patch extraction and federated data distribution.
</p>

---

## 📦 Output Directory Structure

After execution, the generated `patches/` directory should look like:

```text
patches/
├── initial/
├── clients/
│   ├── client_1/
│   ├── client_2/
│   └── ...
│
└── test/
```

---

# 🧠 Step 2 — Federated Model Training

Notebook:

```text
FedLearn_FedFFTNet.ipynb
```

This notebook performs:

- Federated training
- Global aggregation
- Local client optimization
- Source Camera Model classification

---

# ⚙️ Training Configuration

| Variable | Type | Default | Description |
|---|---|---|---|
| `root` | `str` | `./patches` | Patched dataset directory |
| `global_available` | `bool` | `True` | Availability of global server data |
| `batchsize` | `int` | `128` | Training batch size |
| `ROUNDS` | `int` | `100` | Number of communication rounds |
| `CLIENT_EPOCHS` | `int` | `1` | Local client epochs per round |
| `GLOBAL_EPOCHS` | `int` | `30` | Global server training epochs |
| `learning_rate` | `float` | `0.001` | Optimizer learning rate |
| `device` | `str` | `cuda:0` | Training device |

---

# 🏗️ FedFFTNet Architecture

<div align="center">

<img src="images/fedfft_model_architecture.png" alt="FedFFTNet Architecture" width="650"/>

</div>

<p align="center">
<b>Figure 2.</b> Proposed FedFFTNet architecture for federated SCMI.
</p>

---

# 🚀 Running the Pipeline

## Step 1 — Generate Patches

Run:

```bash
Fed_DataSplit_Laplacian.ipynb
```

This creates the federated patch dataset.

---

## Step 2 — Train FedFFTNet

Run:

```bash
FedLearn_FedFFTNet.ipynb
```

This starts federated training across all clients.

---

# 🧪 Supported Data Distribution Modes

| Distribution | Description |
|---|---|
| `equal` | Equal data distribution across all clients |
| `random` | Random client-wise data distribution |
| `skew` | Non-IID skewed distribution |

---

# 📚 Citation

If you use this work in your research, please cite:

```bibtex
@article{chakraborty2025source,
  title={Source Camera Model Identification via Federated Learning using Laplacian-based Patches},
  author={Chakraborty, Rejoy and Goyal, Puneet},
  journal={IEEE Transactions on Artificial Intelligence},
  year={2025},
  publisher={IEEE}
}
```

---

# ⚠️ Disclaimer

This repository is intended strictly for:

- Academic research
- Educational purposes
- Experimental evaluation

---

# 👨‍💻 Authors

- Rejoy Chakraborty
- Puneet Goyal

---

# ⭐ Acknowledgement

If you find this repository useful, consider giving it a ⭐ on GitHub.

---
