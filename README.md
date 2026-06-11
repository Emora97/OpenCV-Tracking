# OpenCV Trajectory Tracking

Computer vision pipeline for tracking and validating Crazyflie 2.1+ flight trajectories using OpenCV, ArUco markers, and markerless object tracking.

## Overview

This repository contains the external vision-based tracking tools developed as part of an undergraduate mechanical engineering research project at the Illinois Institute of Technology.

The software processes recorded flight footage to estimate the drone trajectory independently of the onboard state estimator and compare external measurements against logged Crazyflie flight data.

The project currently supports:

- Camera calibration
- ArUco marker detection and pose estimation
- Markerless object tracking
- Pixel-to-meter conversion
- Video synchronization with flight logs
- Trajectory reconstruction
- Visualization and comparison against onboard EKF estimates

---

## Related Project

Autonomous flight generation and onboard logging are handled by the companion repository:

**Drone Automation:** https://github.com/emora97/Drone-Automation

Together, the two repositories provide a complete experimental workflow:

```
Crazyflie Flight
        │
        ▼
Flight Logs + Video
        │
        ▼
OpenCV Tracking Pipeline
        │
        ▼
Trajectory Validation
Performance Analysis
Visualization
```

---

## Features

- Camera intrinsic calibration
- Lens distortion correction
- ArUco marker detection
- Pose estimation
- Markerless tracking
- Pixel-to-meter scaling
- Time synchronization with Crazyflie logs
- Trajectory comparison

---

## Repository Structure

```text
.
├── calibration/
│   └── Camera calibration scripts
│
├── tracking/
│   └── ArUco and markerless tracking scripts
│
├── comparison/
│   └── Flight log comparison utilities
│
├── data/
│   └── Example CSV files
│
├── media/
│   └── Images and figures
│
├── requirements.txt
└── README.md
```

---

## Requirements

- Python 3.x
- OpenCV
- NumPy
- Pandas
- Matplotlib

Optional:

- SciPy (additional analysis)
- tqdm (progress bars)

---

## Installation

Clone the repository:

```bash
git clone https://github.com/emora97/OpenCV-Tracking.git
cd OpenCV-Tracking
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it:

### Windows

```bash
.venv\Scripts\activate
```

### Linux/macOS

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Workflow

### 1. Camera Calibration

Generate intrinsic calibration parameters using checkerboard images.

Outputs:

- Camera matrix
- Distortion coefficients

---

### 2. Record Flight Video

Capture Crazyflie flight using a stationary camera.

---

### 3. Perform Tracking

Choose one of two approaches:

#### ArUco Tracking

Detects an attached ArUco marker and estimates its position over time.

#### Markerless Tracking

Tracks the drone using user-selected image regions without requiring fiducial markers.

---

### 4. Convert Pixels to Physical Units

Apply the measured calibration scale to convert image coordinates into meters.

---

### 5. Synchronize with Flight Logs

Align tracked video data with onboard Crazyflie CSV logs.

---

### 6. Compare Trajectories

Generate comparison plots between:

- Reference trajectory
- Crazyflie EKF estimate
- OpenCV-derived trajectory

---

## Example Outputs

Typical outputs include:

- Camera calibration files
- Trajectory CSV files
- Position comparison plots
- Error plots
- Overlay visualizations
- Annotated videos

---

## Research Objectives

The goal of this repository is to establish a lightweight external measurement system capable of validating autonomous Crazyflie flight without requiring expensive commercial motion capture systems.

The framework enables quantitative comparison between onboard state estimation and externally observed motion.

---

## Future Improvements

- Multi-camera tracking
- Real-time trajectory estimation
- Automated synchronization
- Low-cost motion capture integration

---

## Acknowledgments

Developed as part of undergraduate research in Mechanical Engineering at the Illinois Institute of Technology using OpenCV and the Bitcraze Crazyflie platform.

---

## License

Released under the MIT License unless otherwise specified.
