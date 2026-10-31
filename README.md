# TurtleBot3 Autonomous Navigation

Autonomous navigation using **TurtleBot3 Burger**, **ROS 2 Humble**, **Gazebo Classic**, and **Navigation2 (Nav2)**.

This repository documents the simulation setup and the steps used to demonstrate goal-based navigation in an obstacle environment.

## Demonstration

A 1–2 minute screen recording showing the robot navigating in Gazebo and RViz will be linked here after it is uploaded:

- **Demo video:** _To be added_

## Environment

| Component | Setup |
|---|---|
| Operating system | Ubuntu 22.04.5 LTS |
| ROS 2 distribution | Humble |
| Robot | TurtleBot3 Burger |
| Simulation | Gazebo Classic |
| Navigation | ROS 2 Navigation2 (Nav2) |
| Localization | AMCL |
| Visualization | RViz2 |
| Simulation time | Enabled (`use_sim_time:=True`) |

## Prerequisites

The following packages and environment should be installed and configured:

- ROS 2 Humble
- Gazebo Classic integration for TurtleBot3
- TurtleBot3 packages, including simulation and navigation
- Nav2 packages
- RViz2

Follow the official TurtleBot3 and ROS 2 installation instructions for package installation appropriate to your system.

## Running the simulation

Open separate terminals and source ROS 2 in each terminal.

### 1. Start the TurtleBot3 Gazebo simulation

Set the robot model:

```bash
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
```

Launch the Gazebo world using the TurtleBot3 Gazebo launch file/world installed on your system. The exact command depends on the world selected for the local setup.

### 2. Start Nav2

In another terminal:

```bash
source /opt/ros/humble/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True
```

### 3. Initialize localization and navigate

1. In RViz2, set the robot's initial pose using **2D Pose Estimate**.
2. Wait for localization to initialize and for the `map → odom` transform to become available.
3. Select **Nav2 Goal**, then click and drag on a free area of the map to set a navigation goal.
4. Observe the planned route and robot motion in Gazebo and RViz2.
5. Confirm arrival through Nav2 feedback and terminal output.

## Verified result

During testing, the following were observed:

- TurtleBot3 Burger spawned successfully in Gazebo.
- Nav2 and localization became active.
- The map topic was published by the map server.
- AMCL established the `map → odom` transform after setting the initial pose.
- A navigation goal completed successfully. The Nav2 terminal reported `Reached the goal!` and `Goal succeeded`.

## Repository contents

```text
.
├── README.md
├── .gitignore
└── docs/
    └── setup-notes.md
```

Configuration files, map assets, screenshots and the demonstration video can be added as they are finalized. Do not commit generated ROS build, install or log directories.

## Notes and limitations

- This project uses existing TurtleBot3 and Nav2 packages; it does not implement a custom path-planning algorithm.
- The map used by the running map server should be identified and included in `maps/` if redistribution is permitted. Testing confirmed that `/map` was published, but the map's provenance has not yet been established.
- The exact Gazebo world launch command and map file path should be added once the local launch configuration and map source are confirmed.

## References

- [TurtleBot3 documentation](https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/)
- [ROS 2 Humble documentation](https://docs.ros.org/en/humble/)
- [Nav2 documentation](https://docs.nav2.org/)