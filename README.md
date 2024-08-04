# TurtleBot Navigation-
 This task involves installing TurtleBot navigation by install turtleBot package , install turtlebot simulation package , create map and launch navigation 

---

## Installation
### Prerequisites 
- In this task i used theconstruct.ai

  
### Install ROS on PC 
```
$ sudo apt update
$ sudo apt upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh
$ chmod 755 ./install_ros_noetic.sh 
$ bash ./install_ros_noetic.sh

```
### Install Dependent ROS package 
```
$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers

```


### Install TurtleBot package  
```
$ sudo apt install ros-noetic-dynamixel-sdk
$ sudo apt install ros-noetic-turtlebot3-msgs
$ sudo apt install ros-noetic-turtlebot3
```
---

![1](https://github.com/user-attachments/assets/7ec2cc75-73c6-42f3-aa63-532c0d4d0b2a)

## Gazebo Simulation :
### Install Simulation package 
```
$ cd ~/catkin_ws/src/
$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```
![2](https://github.com/user-attachments/assets/1bdbce13-8841-43d1-952d-3d4ed25705d0)


### launch Simulation world  
1 - Empty World 
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```
![3](https://github.com/user-attachments/assets/92793929-0490-437f-a731-eabc124bbafc)
---
2 - TurtleBot3 World 
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
3- TurtleBot House
```
$ export TURTLEBOT3_MODEL=waffle_pi
$ roslaunch turtlebot3_gazebo turtlebot3_house.launch
```
![4](https://github.com/user-attachments/assets/ff6c5b2a-3482-4815-b5a9-7083510d75c2)
## Oprate TurtleBot3
```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
---
## SLAM Simulation :
### Launch simulation world  
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
### Run SLAM node :
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
### Run Teleoperation node :
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
![5](https://github.com/user-attachments/assets/315df142-a300-4f2c-bcf5-6f1167726e99)

### Save map :
```
$ rosrun map_server map_saver -f ~/map
```
---
## Navigation Simulation :
### Launch simulation world  
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
### Run Navigation Node  
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```
### Launch keyboard teleoperation node 
```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
--- 



























