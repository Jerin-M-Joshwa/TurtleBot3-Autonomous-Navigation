# TurtleBot3 Autonomous Navigation

Autonomous navigation using **TurtleBot3 Burger**, **ROS 2 Humble**, **Gazebo Classic**, and **Navigation2 (Nav2)**.

This project demonstrates goal-based autonomous navigation in a Gazebo obstacle environment, with localization and navigation visualized in RViz2.

## Demonstration

- **Screen recording (1–2 minutes):** _Link to be added after upload_

## Environment

| Component | Setup |
|---|---|
| Operating system | Ubuntu 22.04.5 LTS |
| ROS 2 | Humble |
| Robot | TurtleBot3 Burger |
| Simulation | Gazebo Classic |
| Navigation | Nav2 |
| Localization | AMCL |
| Visualization | RViz2 |

## Prerequisites

- ROS 2 Humble
- TurtleBot3 simulation and navigation packages
- Gazebo Classic
- Nav2 and RViz2

Install the packages using the official ROS 2 and TurtleBot3 instructions for your environment.

## Run the simulation

Use separate terminals. Source ROS 2 and set the robot model in each terminal.

### 1. Launch Gazebo

```bash
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

### 2. Launch Nav2

```bash
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True
```

Nav2's map server was observed loading the standard map from the installed TurtleBot3 navigation package:

```text
/opt/ros/humble/share/turtlebot3_navigation2/map/map.yaml
```

The map metadata is included in [`maps/map.yaml`](maps/map.yaml), and its image asset `map.pgm` belongs beside it. See [`maps/README.md`](maps/README.md) for source and attribution.

### 3. Initialize localization and send a goal

1. In RViz2, select **2D Pose Estimate** and set the robot's approximate initial pose and heading on the map.
2. Wait for AMCL to initialize and for the `map → odom` transform to become available.
3. Select **Nav2 Goal**, then click and drag on a free area of the map to set a goal pose.
4. Observe the planned route in RViz2 and the robot motion in Gazebo.
5. Confirm arrival through Nav2 feedback and terminal output.

## Verified result

During the test run:

- TurtleBot3 Burger spawned successfully in Gazebo.
- The map server published `/map` and was active.
- Nav2 and localization became active after initialization.
- AMCL established the `map → odom` transform after setting the initial pose.
- A navigation goal completed successfully. The Nav2 terminal reported `Reached the goal!` and `Goal succeeded`.

## Repository structure

```text
.
├── README.md
├── .gitignore
├── docs/
│   └── setup-notes.md
└── maps/
    ├── README.md
    ├── map.yaml
    └── map.pgm  # copy this binary image from the installed package
```

Do not commit generated ROS `build/`, `install/`, or `log/` directories.

## Notes

- This project uses existing TurtleBot3 and Nav2 packages; it does not implement a custom path-planning algorithm.
- The map used during testing was the map installed with the TurtleBot3 Nav2 package, not a map generated with SLAM for this exercise.
- The Gazebo launch command above is the command found in the local shell history. The setup was tested successfully on the configured Ubuntu 22.04.5 / ROS 2 Humble environment.

## References

- [TurtleBot3 documentation](https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/)
- [ROS 2 Humble documentation](https://docs.ros.org/en/humble/)
- [Nav2 documentation](https://docs.nav2.org/)
