# hex_ros_urdf_template

A dual ROS1/ROS2 URDF template package with a 7-DOF serial manipulator robot model.

## Structure

```
hex_ros_urdf_template/
├── CMakeLists.txt           # Auto-detect ROS version, install assets
├── package.xml              # Dual ROS1/ROS2 dependencies
├── config/
│   ├── ros1/display.rviz    # RViz1 configuration
│   └── ros2/display.rviz    # RViz2 configuration
├── launch/
│   ├── ros1/
│   │   ├── display.launch   # Visualize robot in RViz
│   │   └── simulate.launch  # Simulate in Gazebo + RViz
│   └── ros2/
│       ├── display.launch.py
│       └── simulate.launch.py
├── meshes/                  # Placeholder for mesh assets
├── urdf/
│   ├── model.urdf           # 7-DOF arm URDF description
│   └── sim_base.xacro       # Xacro for Gazebo simulation
└── README.md
```

## Usage

### ROS1 (build with catkin_make or catkin build)

```bash
# Display in RViz
roslaunch hex_ros_urdf_template display.launch

# Simulate in Gazebo
roslaunch hex_ros_urdf_template simulate.launch
```

### ROS2 (build with colcon)

```bash
# Display in RViz2
ros2 launch hex_ros_urdf_template display.launch.py

# Simulate in Gazebo
ros2 launch hex_ros_urdf_template simulate.launch.py

# Turn off visualization
ros2 launch hex_ros_urdf_template display.launch.py visual:=false
```

## Robot Model

The package models a 7-DOF serial manipulator arm with 8 links:

| Link | Type | Description |
|------|------|-------------|
| base_link | fixed | Base plate |
| link_1 ~ link_7 | actuated | Serial chain links driven by revolute joints |

Joint axes alternate between Z and Y axes, providing 7 degrees of freedom suitable for reaching arbitrary poses within the workspace.
