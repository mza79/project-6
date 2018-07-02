# Project

## File Architecture
```
catkin_ws/
  src/
    project/                    ← this git repository
      robot_control_pkg/        ← package
        CMakeList.txt
        package.xml
      robot_description_pkg/    ← package
      robot_simulation_pkg/     ← package
      central_control_pkg/      ← package
```

## Usage command

### Simulation in gazebo

```sh
$ roslaunch robot_simulation_pkg simulation.launch
```

### Use keyboard control robot

```sh
$ roslaunch robot_simulation_pkg simulation_one_robot.launch
$ roslaunch robot_control_pkg keyboard_teleop.launch
```

### Use web control robot

```sh
$ roslaunch rosbridge_server rosbridge_websocket.launch
$ roslaunch robot_simulation_pkg simulation.launch
```

+ Open web page and input IP address.

### Open zbar example launch

+ Need to install zbar `sudo apt-get install ros-indigo-zbar-ros`

```sh
$ roslaunch zbar_ros_pkg example.launch
```

### Navigation

```sh
$ roslaunch robot_simulation_pkg simulation_one_robot.launch
$ roslaunch robot_navigation_pkg amcl.launch
$ rviz
$ rostopic pub /move_base_simple/goal geometry_msgs/PoseStamped '{header: {stamp: now, frame_id: "map"}, pose: {position: {x: 1.0, y: 0.0, z: 0.0}, orientation: {w: 1.0}}}'
```

### Watch map on web

```sh
$ roslaunch rosbridge_server rosbridge_websocket.launch
$ roslaunch robot_simulation_pkg simulation_one_robot.launch
$ roslaunch robot_navigation_pkg amcl.launch
```

### Central control

```sh
$ roslaunch central_control_pkg control.launch
# test
$ rostopic echo /move_base_simple/goal
$ rostopic pub /speaker std_msgs/String 1:a     
$ rostopic pub /barcode std_msgs/String "'1'"
```
