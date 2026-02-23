# RGBD-Yaw-Alignment-Info
Research overview and documentation for the geometry-driven RGB-D yaw alignment pipeline (code available upon publication).

# RGBD-Yaw-Alignment

Reference implementation for the paper:

“A Geometry-Driven, Explainable RGB-D Vision Pipeline for Real-Time Yaw Alignment in Low-Cost Robotic Systems”  


## Overview
This repository provides a research implementation of a closed-form, uncertainty-aware RGB-D yaw alignment pipeline designed for CPU-only deployment in cost-constrained robotic systems.

The framework integrates:

- Percentile-based depth-band segmentation
- Line-based orientation extraction (Hough + PCA fallback)
- 2θ circular statistics aggregation
- IQR-based temporal stabilization with lock-on hysteresis
- Two-point affine yaw calibration
- Safe motion execution strategy

The implementation follows the analytical formulation described in the manuscript and supports reproducibility of the reported experiments.

## Key Characteristics

- Fully closed-form geometric pipeline
- Explicit first-order uncertainty propagation
- No deep learning models required
- No GPU acceleration required
- Designed for consumer-grade RGB-D sensors
- Real-time execution (~40 ms/frame on CPU)


## Hardware Used in Experiments

- Intel RealSense RGB-D camera
- xArm robotic manipulator
- Desktop-class CPU (no GPU acceleration)

The code can be adapted to other RGB-D cameras and manipulators with minor modifications.


## Requirements
Python 3.9+
Required packages:
- OpenCV
- NumPy
- SciPy
- pyrealsense2
- xArm SDK (if robot control is enabled)

Before running the system: Update robot IP address in the script ROBOT_IP = "192.168.xxx.xxx"

## Reproducibility Notes

All experiments were performed under indoor illumination (~500 lx)

Camera height: 0.45 m
Camera tilt: 25°
CPU-only execution
No external lighting control
No GPU acceleration
For exact replication, match the above configuration.

## Disclaimer
This repository provides a research reference implementation.
It is not production-grade industrial control software.
Safety checks and hardware validation are required before real-world deployment.
