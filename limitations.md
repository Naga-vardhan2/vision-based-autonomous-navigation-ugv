# Limitations and Development Notes

## Known limitations

- Simulation performance decreases under heavy scenes.
- RGB-D depth quality can be affected by lighting and texture.
- AMCL requires a known map.
- Visual odometry is not part of the current stable localization pipeline.
- Dynamic environments need to stay within available computational resources.
- Real-world deployment would require hardware integration and sensor calibration.

## Development issues documented in the project

### Duplicate controllers / TF
Cause: orphan Gazebo/controller processes.

Fix: clean shutdown and process cleanup; verify a single controller and odometry publisher.

### RViz robot/map missing
Cause: broken `map → odom → base_link` chain and map QoS mismatch.

Fix: activate AMCL/map server, repair TF, and use Transient Local for map display.

### Robot not moving
Cause: solid START marker physically blocked the spawn point.

Fix: use a non-blocking ground pad/high beacon.

### False safety stops
Cause: collision-monitor polygon did not match the UGV footprint.

Fix: adjust the safety polygon to the actual chassis footprint.

### Recovery command path
Cause: recovery behavior could publish to a different `/cmd_vel` route.

Fix: route behavior commands through `/cmd_vel_nav` and collision_monitor.
