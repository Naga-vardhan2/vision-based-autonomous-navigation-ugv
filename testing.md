# Testing

## Test Matrix

| Test | Expected result |
|---|---|
| Basic bring-up | Gazebo, UGV, controllers and sensors start |
| A → B navigation | UGV accepts Nav2 goal and moves toward destination |
| Dynamic obstacle | Costmaps update and route is replanned |
| Camera hazard | Camera hazard points cause a safe detour |
| Ditch test | Depth drop-off generates a safety boundary |
| Regression | Fixed environment remains a repeatable baseline |

## Verification Commands

```bash
ros2 control list_controllers
ros2 topic info /scan
ros2 action list | grep navigate_to_pose
```

## Camera Hazard Test

The documented test observed a rock, published hazard points on:

```text
/camera/hazard_points
```

Nav2 then marked lethal costmap cells and changed the UGV trajectory.

## Dynamic Obstacle Test

LiDAR/camera observe the obstacle, the obstacle enters the costmap, and Nav2 calculates a new path while the collision monitor remains active.
