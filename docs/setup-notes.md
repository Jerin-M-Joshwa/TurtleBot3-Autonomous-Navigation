# Setup notes

## Known working configuration

- Ubuntu 22.04.5 LTS
- ROS 2 Humble
- TurtleBot3 Burger
- Gazebo Classic
- Nav2 with simulation time enabled

## Launching Gazebo

Run in a terminal:

```bash
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

## Launching Nav2

Run in another terminal:

```bash
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True
```

## Map source observed during testing

Nav2's map server reported this installed map YAML:

```text
/opt/ros/humble/share/turtlebot3_navigation2/map/map.yaml
```

The YAML references `map.pgm`. The repository includes the YAML metadata in `maps/map.yaml`; place the matching `map.pgm` image in the same directory. See [`maps/README.md`](../maps/README.md) for map metadata and upstream attribution.

The map server was active and `/map` published an OccupancyGrid. This map was supplied by the installed TurtleBot3 Nav2 package; it was not generated with SLAM for this exercise.

## Localization and navigation checklist

1. Confirm that the map server is active and `/map` publishes an OccupancyGrid.
2. In RViz2, use **2D Pose Estimate** to initialize AMCL.
3. Confirm the `map → odom` transform is available.
4. Send a goal using **Nav2 Goal**.
5. Verify the controller reports goal completion.

## Remaining repository work

- `maps/map.pgm` and `maps/map.yaml` have been committed to the public repository.
- Add selected screenshots from the actual simulation.
- Add the public demo video link after upload.
- Re-test the README instructions from a clean terminal/session.
