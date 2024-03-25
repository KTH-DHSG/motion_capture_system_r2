# motion_capture_system_r2

Package for using the motion capture system with ROS2. Use [motion_capture_system](https://github.com/KTH-DHSG/motion_capture_system) for use with ROS1.

## How to use

Requisites: qualisys_cpp_skd

Create workspace:
```
mkdir -p mocap_ws/src && cd mocap_ws/src
```
Download qualisys repo recursively to get https://github.com/qualisys/qualisys_cpp_sdk, or set QualisysSDK_PATH:
```
git clone --recursive https://github.com/KTH-DHSG/motion_capture_system_r2.git
```
Install dependencies:
```
vcs import < motion_capture_system_r2/dependency_repos.repos
```
Compiling workspace:
```
cd .. && colcon build --symlink-install
```
Source workspace:
```
source install/setup.bash
```
Setup your qualisys configuration (qualysis server IP is 10.0.0.10):
```
mocap_ws/src/mocap4ros2_qualisys/qualisys_driver/config/qualisys_driver_params.yaml
```
Launch qualisys system:
```
ros2 launch qualisys_driver qualisys.launch.py
```
Visualize in rViz (not working at the moment):
```
ros2 launch mocap_marker_viz mocap_marker_viz.launch.py mocap_system:=qualisys
```

## Published topics

- /qualisys/{subject_name}/pose ([geometry_msgs/PoseStamped](http://docs.ros.org/en/api/geometry_msgs/html/msg/PoseStamped.html))
