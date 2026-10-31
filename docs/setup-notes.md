# Setup notes

## Known working configuration
- Ubuntu 22.04.5 LTS
- ROS 2 Humble
- TurtleBot3 Burger
- Gazebo Classic
- Nav2 with simulation time enabled

## Launching Nav2

```bash
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True
```

## Localization checklist
1. Confirm that the map server is active and `/map` publishes an OccupancyGrid.
2. In RViz2, use **2D Pose Estimate** to initialize AMCL.
3. Confirm the `map → odom` transform is available.
4. Send a goal using **Nav2 Goal**.

## To finalize
- Record the exact Gazebo world launch command used.
- Identify the map YAML/image source and include it if permitted.
- Add screenshots and the public demo video link.
- Verify the README instructions from a clean terminal/session.
