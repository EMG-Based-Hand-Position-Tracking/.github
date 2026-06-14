# Hardware Accelerated AI Model for EMG-Based Hand Position Tracking

This project was done as a Senior Year Capstone Design Project in the Department of Electrical and Computer Engineering, Dhanani School of Scienc and Engineering, Habib University by [Abdullah Amir](https://github.com/aa08453), [Muhammad Quddusi Kashaf](https://github.com/Quddusi-K) and [Saif Nazir](https://github.com/saif-1219).

This work presents a hardware-software co-design framework that addresses both limitations simultaneously. A custom RoFormer architecture, a Transformer augmented with Rotary Positional Embeddings, is trained on the NinaPro sEMG dataset to regress 10 independent joint angles per sliding window, capturing the full kinematic envelope required for functional grasping. To enable edge deployment, the model undergoes Quantization-Aware Training (QAT), compressing weights to 8-bit integers without degrading regression accuracy.

The quantized model is accelerated on a Xilinx Zynq-7000 SoC (ZedBoard) using Vitis High-Level Synthesis. The hardware implementation exploits M_AXI burst-mode memory access to eliminate the memory-wall bottleneck common in naive FPGA deployments, achieving deterministic, jitter-free inference. The FPGA fabric operates in fixed-point arithmetic using ap_fixed precision types, validated through C/RTL co-simulation prior to hardware deployment.

Predicted joint trajectories are streamed via UART to a Unity 3D Digital Twin, where a Kalman filter smooths output kinematics into anatomically plausible motion. Hardware resource utilization on the Zynq-7000 reached 95% BRAM, 100% DSP, and 26% LUT occupancy, confirming that the design is computationally dense and well-matched to the target device.

The result is a self-contained, wearable-ready inference pipeline that bridges the gap between laboratory biomechanics and deployable prosthetic hardware — demonstrating that Transformer-based continuous kinematic estimation is viable on commodity FPGA platforms without cloud dependency.

 
