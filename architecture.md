# System Architecture

## 1. Perception

The RGB-D camera provides RGB and depth information. Depth is converted from image coordinates into 3D points relative to the robot.

The perception logic classifies points into:

- traversable ground
- positive obstacles such as rocks, trees and logs
- negative obstacles such as ditches

LiDAR provides a 360° distance scan for obstacle detection and safety.

## 2. Localization

The stable navigation pipeline uses:

- known map
- AMCL
- wheel odometry
- TF

The main TF chain is:

```text
map
 ↓
odom
 ↓
base_link
 ↓
camera / LiDAR / IMU / wheels
```

## 3. Navigation

Nav2 receives the map, localization information and obstacle information.

Its flow is:

```text
Goal
 ↓
Global path
 ↓
Local path
 ↓
Safety check
 ↓
Motor command
```

When an obstacle blocks the path, the costmap is updated and Nav2 replans.

## 4. Motion

ROS 2 `ros2_control` exposes wheel control through the differential-drive controller. The robot receives velocity commands and converts them into wheel motion.

## 5. Master Launch

The documented master launch sequence starts:

1. Gazebo/world
2. UGV
3. robot_state_publisher and bridge
4. controllers
5. Nav2/lifecycle nodes
6. camera perception
7. RViz
8. optional dynamic environment manager
