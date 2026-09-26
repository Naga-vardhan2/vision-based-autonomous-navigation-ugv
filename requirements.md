# Requirements

## Operating System

- Ubuntu 24.04

## ROS

- ROS 2 Jazzy
- Nav2
- RViz2
- ros2_control
- Gazebo ROS integration

## Simulation

- Gazebo Harmonic

## Robot Components

- Four driven wheels
- RGB-D camera
- 360° LiDAR
- IMU
- Wheel odometry

## Key Robot Parameters

- Approximate base size: 0.80 m × 0.55 m
- Wheel radius: 0.13 m
- Wheel separation: 0.58 m

## ROS Interfaces

- Velocity command: `Twist` / `TwistStamped`
- Odometry: `/diff_drive_controller/odom`
- Camera hazard points: `/camera/hazard_points`
