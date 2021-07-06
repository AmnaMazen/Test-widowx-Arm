# Test-widowx-Arm

Author name: Amna Mazen Ali

This file is a tutorial for testing the joints of widowx_Arm
by three methods.



# Method 1: Using Arbotix_python package

The arbotix_python package provides a basic ROS interface to an ArbotiX RoboController over a USB serial connection, or XBEE wireless radios.

This package consists of three tools: the driver, a GUI for interacting with the driver, and a terminal tool for setting up your servos.

1- Go to source file inside "widowx" workspace.

$ cd ~/widowx/src

2- Clone Arbotix_python package:

$ git clone https://github.com/vanadiumlabs/arbotix_ros.git

3- source ROS workspace "widowx"

$ cd ..

$ catkin_make

$ source ./devel/setup.bash

4- Change permission to access the port of widowx_arm

$ chmod 777 /dev/ttyUSB0

$ arbotix_terminal 

$ ls

If the IDs of all joints are identified correctly you should get 

1 2 3 4 5 6 .. .. .. .. 

Which means it identifies the 6 joints of the arm. 

# Method 2: Direct commands to joints


sending direct commands to move , relax and enable joints


# Method 3: Create a ROS package that sends different commands to each joint

