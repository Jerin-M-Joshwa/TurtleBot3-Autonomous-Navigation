# Map assets

The navigation test used the standard map installed with the ROS 2 Humble TurtleBot3 Nav2 package.

Source directory on the test machine:

```text
/opt/ros/humble/share/turtlebot3_navigation2/map/
```

Both map files are kept together:

- `map.yaml` — occupancy grid metadata
- `map.pgm` — occupancy grid image referenced by `map.yaml`

Map metadata from the installed YAML:

| Parameter | Value |
|---|---|
| Resolution | 0.05 m/pixel |
| Origin | `[-10.0, -10.0, 0.0]` |
| Negate | `0` |
| Occupied threshold | `0.65` |
| Free threshold | `0.196` |

The map was supplied by the installed TurtleBot3 Nav2 package; it was not generated with SLAM for this exercise. The ROS package index lists `turtlebot3_navigation2` under the Apache 2.0 license. Preserve upstream attribution and license notices when redistributing package assets: [ROS package overview](https://index.ros.org/p/turtlebot3_navigation2/).
