# Map assets

The navigation test used the standard map installed with the ROS 2 Humble TurtleBot3 Nav2 package.

Source directory on the test machine:

```text
/opt/ros/humble/share/turtlebot3_navigation2/map/
```

The map YAML references the image by the relative filename `map.pgm`. Keep both files together in this directory:

- `map.yaml` — occupancy grid metadata
- `map.pgm` — occupancy grid image

Map metadata from the installed YAML:

| Parameter | Value |
|---|---|
| Resolution | 0.05 m/pixel |
| Origin | `[-10.0, -10.0, 0.0]` |
| Negate | `0` |
| Occupied threshold | `0.65` |
| Free threshold | `0.196` |

The map was supplied by the installed TurtleBot3 Nav2 package; it was not generated with SLAM for this exercise. Check package and asset redistribution terms before publishing the copied files.
