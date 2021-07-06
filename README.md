# Test-widowx-Arm

Author name: Amna Mazen Ali

This file is a tutorial for testing the joints of widowx_Arm by two methods.







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

In this method, you need to launch controller already cloned in this tutorial: https://github.com/AmnaMazen/widowx-arm-ready-to-work-with-ROS

To launch widowx-arm  controller:

  $ cd ~/widowx

  $ source ./devel/setup.bash

  $ roslaunch widowx_arm_controller widowx_arm_controller.launch

In this method, direct commands will be sent to the joints with specific values via ROS topic and to enable/relax the joints and set specific speed using ROS services


To check all available topic run:

  $ rostopic list
  
  
# Send commands

To send a specific data to a certain joint use the corresponding <topic-name>. Here is command to send "data: 0.0" to all joints
  
  $ rostopic pub /joint_1/command std_msgs/Float64 "data: 0.0" 
  
  $ rostopic pub /joint_2/command std_msgs/Float64 "data: 0.0" 
  
  $ rostopic pub /joint_3/command std_msgs/Float64 "data: 0.0" 
  
  $ rostopic pub /joint_4/command std_msgs/Float64 "data: 0.0" 
  
  $ rostopic pub /joint_5/command std_msgs/Float64 "data: 0.0" 
  
  $ rostopic pub /gripper_revolute_joint/command std_msgs/Float64 "data: 0.0" 
  
  $ rostopic pub /gripper_prismatic_joint/command std_msgs/Float64 "data: 0.0"

Dynamixel motors work within the angular range [-pi/2, pi/2], thus the commands that can be sent to joints (1-5) must be within this range.
  
Gripper works in a different way of prismatic motion and it uses values between 0 and 0.05.
  
To check all available services run:
  
  $ rosservice list
  
# Relax Joints
  
To relax the joints, call the following ROS services:
  
  $ rosservice call /joint_1/relax
  
  $ rosservice call /joint_2/relax
  
  $ rosservice call /joint_3/relax
  
  $ rosservice call /joint_4/relax
  
  $ rosservice call /joint_5/relax
  
  $ rosservice call /gipper_revolute_joint/relax
  
  
# Enable joints
  
To enable the joints, call the following ROS services:
  
  $ rosservice call /joint_1/enable True
  
  $ rosservice call /joint_2/enable True
  
  $ rosservice call /joint_3/enable True
  
  $ rosservice call /joint_4/enable True
  
  $ rosservice call /joint_5/enable True
  
  $ rosservice call /gipper_revolute_joint/enable True
  

# Set speed of motors  
  
To set the speed of motors:
  
  $ rosservice call /joint_1/set_speed 1
  
  $ rosservice call /joint_2/set_speed 1
  
  $ rosservice call /joint_3/set_speed 1
  
  $ rosservice call /joint_4/set_speed 1
  
  $ rosservice call /joint_5/set_speed 1
  
  $ rosservice call /gipper_revolute_joint/set_speed 1
  
  

 





