

# [Doosan Robotics](http://www.doosanrobotics.com/kr/)<img src="https://user-images.githubusercontent.com/47092672/97660147-142f1f00-1ab4-11eb-9d14-48f30a666cdc.PNG" width="10%" align="right">
[![license - apache 2.0](https://img.shields.io/:license-Apache%202.0-yellowgreen.svg)](https://opensource.org/licenses/Apache-2.0)
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)
[![support level: community](https://img.shields.io/badge/support%20level-community-lightgray.png)](http://rosindustrial.org/news/2016/10/7/better-supporting-a-growing-ros-industrial-software-platform)
# Overview
    
    This package provides the function to control all models of Doosan robots in the ROS2(Humble) environment.
    
    ※ Currently, ROS2 related packages are being updated rapidly. 
       Doosan packages will also be updated from time to time and features will be upgraded.
 

# Installation 
#### *Doosan Robot ROS2 Package is implemented at ROS2-humble.*
    ### Prerequisite installation elements before package installation
    $ sudo apt-get install libpoco-dev libyaml-cpp-dev
    $ sudo apt-get install ros-humble-control-msgs ros-humble-realtime-tools ros-humble-xacro ros-humble-joint-state-publisher-gui ros-humble-ros2-control ros-humble-ros2-controllers ros-humble-gazebo-msgs ros-humble-moveit-msgs
    
    ### We assume that you have installed the ros-humble-desktop package using the apt-get command.
    ### We recommand the /home/<user_home>/ros2_ws/src
    $ mkdir -p ~/ros2_ws/src
    $ cd ~/ros2_ws/src
    $ git clone -b humble-devel https://github.com/doosan-robotics/doosan-robot2.git
    $ git clone https://github.com/ros-controls/gz_ros2_control
    $ rosdep install -r --from-paths . --ignore-src --rosdistro $ROS_DISTRO -y
    $ cd ~/ros2_ws
    $ colcon build
    $ . install/setup.bash


# Tutorial
## 0. Mode Option
### Real Mode 
Use __real mode__ to drive a real robot   
The default IP of the robot controller is _192.168.127.100_ and the port is _12345_.

### Virtual Mode
Use __dsr_emulator__ to drive a virtual robot.
The default IP of the virtual emulator is _127.0.0.1_ and the port is _12345_.

### Launch Parameters
#### *name* 
Robot Namespace (Default dsr01)
#### *host* 
Robot Ip Address (Default 192.168.137.100)
#### *port* 
Robot Port (Default 12345)
#### *mode* 
virtual/real 
#### *model*
Model Inforamtion (Doosan robot model name)
#### *color*
Select WHile/Blue (Only WHile in case of E0609)
#### *gui*
Activate/Deactivate GUI (true/false)
#### *gz*
Activate/Deactivate Gazebo Sim (true/false) 



## 1. Robot Visualization 
### Run Rviz2
```bash
$ ros2 launch dsr_bringup2 dsr_bringup2_rviz.launch.py mode:=real host:=192.168.137.100 model:=m1013
```


## 2. Gazebo Sim 
### Run Gazebo Sim
```bash
$ ros2 launch dsr_bringup2 dsr_bringup2_gazebo.launch.py mode:=real host:=192.168.137.100 model:=m1013
```

## 3. Moveit2 
### Run Moveit2
#### Caution : If you use Moveit2 function, Controller version should be required over 2.12.
```bash
$ ros2 launch dsr_bringup2 dsr_bringup2_moveit2.launch.py mode:=real host:=192.168.137.100 model:=m1013
```

## 4. Nvidia Issac Sim (TBD)
