turtlebot_create
======

It keeps iRobot Create specific packages

# Install instructions for EGOKITUZ lab

The following instructions assume the following setup: 
- ROS Noetic running on Ubuntu 20.05
- Kobuki + Turtlebot2 and all their dependencies already installed from source and configured to run on ROS Noetic with a Kobuki base, an Intel RealSense D435 depth camera, and an YDLIDAR X4 laser.
- (check https://github.com/xabigarde/ for related repositories)

1. Download the turtlebot_create ROS package sources into your workspace and catkin_make:
```
cd ~/turtlebot2_ws/src
git clone https://github.com/xabigarde/turtlebot_create
cd ..
catkin_make
source devel/setup.bash
```
2. Install dependecies:
```
sudo apt install python3-pip
pip install pyserial
```
3. Configure ROS launch variables:
In your .bashrc file, ensure that the following variables are correctly set:
```
export TURTLEBOT_BASE=create
export TURTLEBOT_STACKS=circles
export TURTLEBOT_3D_SENSOR=d435
export TURTLEBOT_BATTERY=None
export TURTLEBOT_LIDAR=false
export TURTLEBOT_SERIAL_PORT=/dev/ttyUSB0
```
4. You may need to add your user permission to write to /dev/ttyUSB0:
```
# Replace username with your user
sudo adduser username dialout
```
To test the installation:
Make sure you have connected the USB to the PC and the serial bus to the robot. Then power on the robot by pressing the power-on button, and then run:
```
roslaunch turtlebot_bringup minimal.launch
```
After a few seconds, the robot should beep, and everything should be set. You should now be able to teleop the robot with the keyboard:
```
roslaunch turtlebot_teleop keyboard_teleop.launch
```
