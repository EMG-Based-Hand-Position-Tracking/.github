## Hi there 👋 Welcome to the EMG Hand Tracking Project

This organization hosts the complete hardware-software co-design framework developed as a Senior Year Capstone Design Project in the Department of Electrical and Computer Engineering, Dhanani School of Science and Engineering, Habib University. 

Our work bridges the gap between laboratory biomechanics and deployable prosthetic hardware by enabling Transformer-based continuous kinematic estimation on edge-FPGA devices without cloud dependency.

### 🚀 Our Project Architecture

Our system splits cleanly into two interconnected domains across our core repositories:

```text
  [ sEMG Signals ]
          │ 
          ▼
┌──────────────────────────────────┐      ┌──────────────────────────────────┐
│      📦 hardware-ai-core         │      │      📦 unity-visualization      │
├──────────────────────────────────┤      ├──────────────────────────────────┤
│ • Quantized RoFormer (8-bit QAT) │      │ • 3D Digital Twin (Unity)        │
│ • Vitis HLS Hardware Accelerator │ ───> │ • Kalman Filter Trajectory       │
│ • Zynq-7000 SoC (Zedboard)       │ UART │ • Smoothing                      │
└──────────────────────────────────┘      └──────────────────────────────────┘

```

---

### 🛠️ Core Repositories

* **[hardware-ai-core](https://github.com/EMG-Based-Hand-Position-Tracking/Hardware-AI)**: Contains the PyTorch training scripts, Quantization-Aware Training (QAT) configurations, Vitis HLS C++ design, and the RTL deployment configurations for the Xilinx Zynq-7000 SoC (ZedBoard).
* **[unity-visualization](https://github.com/EMG-Based-Hand-Position-Tracking/Visualization)**: Contains the Unity 3D engine assets, C# UI scripts, serial communication, and the Kalman filtering logic.

---

### 👩‍💻 The Engineering Team

This capstone project was conceptualized, designed, and optimized by:

* **Abdullah Amir** – [@aa08453](https://github.com/aa08453)
* **Muhammad Quddusi Kashaf** – [@Quddusi-K](https://github.com/Quddusi-K)
* **Saif Nazir** – [@saif-1219](https://github.com/saif-1219)

---

### 🍿 Technical Quick Facts

* **Model Architecture:** Custom RoFormer (Transformer with Rotary Positional Embeddings) trained on the NinaPro sEMG dataset to regress 10 independent joint angles.
* **Hardware Precision:** Evaluated using custom `ap_fixed` precision types via QAT, avoiding accuracy degradation while dropping to 8-bit integers.
* **Resource Maximization:** Highly dense compilation reaching **100% DSP** and **95% BRAM** utilization on the Zynq-7000 fabric through advanced M_AXI burst memory mappings.
* **Data Flow:** Low-latency inference data is passed as packed streaming frames via UART directly to a C# thread inside the Unity environment.

---

### 🌈 Contribution & Usage Guidelines

This project is open for academic and open-source research extensions.

1. If you are extending our hardware blocks, please review the `config.h` in the hardware repository to match your sequence lengths and dimension metrics.
2. For bug reports or feature requests regarding the data-packet stream protocols, please open an issue directly in the respective repository.
