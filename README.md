# Field and Service Robotics - Homework 2

**University of Naples Federico II**  
Master's Degree in Automation and Robotics Engineering

**Student:** Emanuela Varone  
---

## Overview

This repository contains the solutions for Homework 2 of the Field and Service Robotics course. The homework focuses on path planning, trajectory tracking, and control strategies for unicycle robots.

## Repository Structure

```
Field_and_Service_Robotics_HW2/
├── README.md
├── Report_HW2_FSR.pdf
├── Point_1/
│   ├── Point_1_HW2.mlx
│   └── VIDEO/
│       └── robot_animation.mp4
├── Point_2/
│   ├── Point_2_HW2.mlx
│   └── Point2_IO_Linearization_HW2.slx
├── Point_3/
│   ├── Point_3_HW2.mlx
│   └── Point_3.slx
└── Point_4/
    ├── Point_4_HW2.mlx
    ├── Point_4.slx
    └── VIDEO/
        └── unicycle_motion.mp4
```

## Topics Covered

### 1. Path Planning Algorithm for a Unicycle
Implementation of a smooth trajectory generator that drives a unicycle from an initial configuration to a random final configuration while respecting velocity constraints:
- Linear velocity: |v(t)| ≤ 0.5 m/s
- Angular velocity: |ω(t)| ≤ 2 rad/s

**Key features:**
- Polynomial path parameterization
- Time scaling algorithm for constraint satisfaction
- Path and orientation visualization

### 2. Input/Output Linearization Control
Implementation of an I/O linearization control approach for unicycle position control using a virtual output point B located along the robot's sagittal axis.

**Analysis includes:**
- Comparison of three different values of parameter b (-1.0, 0.2, 0.8)
- Tracking accuracy evaluation
- Velocity profile analysis
- Error analysis for Point B

### 3. Linear and Nonlinear Controllers for Bernoulli Lemniscate Trajectory
Design and performance analysis of two control approaches for trajectory tracking:
- Linear controller based on approximate linearization
- (Almost) Nonlinear controller with adaptive gains

**Testing scenarios:**
- r₁ = 2.0 (larger scale trajectory)
- r₂ = 0.2 (smaller scale trajectory)

**Trajectory equation:**
```
x_d(t) = r·cos((α+1)t) / (1 + sin²((α+1)t))
y_d(t) = r·cos((α+1)t)·sin((α+1)t) / (1 + sin²((α+1)t))
```
where α = 4 (last digit of matriculation number)

### 4. Unicycle Posture Regulator with Runge-Kutta Odometry
Implementation of a posture regulator based on polar coordinates with Runge-Kutta odometric localization.

**Objective:** Drive the unicycle from initial configuration q_i = [5, 1, π/4]ᵀ to target q_f = [0, 0, 0]ᵀ

**Key components:**
- Polar coordinate transformation
- Control law generation
- Unicycle kinematic model
- Runge-Kutta numerical integrator

## Requirements

- MATLAB R2020a or later
- Simulink
- Symbolic Math Toolbox

## Usage

Each point folder contains:
- A MATLAB Live Script (`.mlx`) for initialization, simulation parameters, and result visualization
- A Simulink model (`.slx`) for control system implementation (where applicable)

To run the simulations:

1. Open MATLAB and navigate to the desired point folder
2. Open the `.mlx` file
3. Run all sections sequentially
4. For Simulink models, the `.mlx` script will automatically configure and run the simulation

## Key Results

| Point | Controller Type | Key Finding |
|-------|----------------|-------------|
| 1 | Path Planning | Time scaling from 10s to 12.54s ensures velocity constraints |
| 2 | I/O Linearization | b = 0.2 provides optimal tracking accuracy |
| 3 | Linear vs Nonlinear | Nonlinear controller shows better performance, especially for r = 0.2 |
| 4 | Polar Regulator | Target reached in 6.41s with position error < 0.001m |

## Videos

The repository includes demonstration videos:
- `Point_1/VIDEO/robot_animation.mp4` - Path planning trajectory execution
- `Point_4/VIDEO/unicycle_motion.mp4` - Posture regulation to target

## License

This project is for educational purposes as part of the Field and Service Robotics course at University of Naples Federico II.
