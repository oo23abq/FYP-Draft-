# FPGA-Based Enhancements to Quadcopter Control and Sensing Architectures

## Project Overview
This repository contains the RTL design, testbenches, and hardware verification files for an engineering Final Year Project (FYP) investigating FPGA-based flight control architectures. 

Modern quadcopters rely heavily on sequential microcontroller units (MCUs) that are prone to interrupt latency and loop jitter. This project implements a fully concurrent, deterministic flight control pipeline in VHDL targeting the Digilent Basys 3 development board to achieve low-latency sensor fusion and parallel control calculations.

---

## Architecture Pipeline
The system replaces traditional sequential software loops with dedicated, pipelined hardware modules

* **Sensor Interface:** Hardware SPI/I2C state machine reading 6-DOF IMU accelerometer and gyroscope registers.
* **Sensor Fusion:** Pipelined fixed-point complementary filter mapped to FPGA DSP slices for deterministic attitude estimation.
* **Control Loop:** Parallel discrete PID controllers computing multi-axis corrections concurrently.
* **Actuator Generation:** Deterministic PWM / digital ESC protocol generator providing motor drive signals.

---

## Hardware & Software Stack
* **Target Device:** Digilent Basys 3 (Xilinx Artix-7 XC7A35T)
* **Sensor Breakout:** 6-DOF IMU (e.g., MPU-6050 / BMI088 via Pmod headers)
* **Testbed:** Benchtop Hardware-in-the-Loop (HIL) test stand (no free-flight airframe)
* **Design Suite:** AMD Xilinx Vivado Design Suite
* **HDL:** VHDL-2008
* **Verification:** Behavioural simulation testbenches and logic analyser / oscilloscope hardware verification

## Repository Structure
```text
├── constrs/        # Xilinx Design Constraints (.xdc) for Basys 3
├── doc/            # System block diagrams, reports, and CPR meeting records
├── rtl/            # Synthesizable VHDL source files
├── scripts/        # Reference mathematical models and test vector generators
└── sim/            # VHDL simulation testbenches
├── rtl/            # Synthesizable VHDL source files
├── scripts/        # Reference mathematical models and test vector generators
└── sim/            # VHDL simulation testbenches
