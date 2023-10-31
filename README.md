# Fetch-Robot-Grasping

University of Technology Sydney, Australia.
Assignment for 41014 Sensors and Control for Mechatronic Systems subject, Spring 2023 session

Group Members:
 - James Kwan   
 - Sagar Rathi  
 - Aidan Sing    
 
Subject coordinator: Dr. Liang Zhao

Contribution: 
 - James Kwan - 30%
 - Sagar Rathi - 30%
 - Aiden Sing - 40%

## 1) Project Description: ##
Control the Fetch robot to grasp the object on the table, e.g. can of coke, box of cookies, using the robotic arm and hand by
using visual servoing method. Depth images and/or RGB images can be used for the visual servoing. The end-effector of the robot arm has been calibrated with the RGB-D camera.

Target: The Fetch robot grasps different interested objects on the table without falling down.

## 2) Installation ##

### 2.0) Ubuntu 18.04 LTS (Bionic Beaver)

The following proceures assume you have Ubuntu 18.04 LTS installed on your machine. Download it from the [releases page](http://releases.ubuntu.com/).
 
### 2.1) ROS Melodic Installtion 

We will be using ROS Melodic on Ubuntu 18.04 LTS (Bionic Beaver). Follow the instructions at the [ROS Melodic installation instructions page.](https://wiki.ros.org/melodic/Installation/Ubuntu)

A summary of the commands is showed below:

1) `sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list`

2) `sudo apt install curl # if you haven't already installed curl
    curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add`
   
3) `sudo apt-get update`

4) `sudo apt-get install ros-melodic-desktop-full`

5) `sudo rosdep init`

6) `rosdep update`

7) `echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc`

8) `source ~/.bashrc`

### 3) Fetch Robot

[Official documentation page](https://docs.fetchrobotics.com/).

#### 3.1) Install Gazebo simulator Demo
`sudo apt install ros-melodic-fetch-calibration ros-melodic-fetch-open-auto-dock \
 ros-melodic-fetch-navigation ros-melodic-fetch-tools -y`

#### 3.2) Install the main package from Fetch Robotics GitHub page

Go to your ROS workspace, and do the following commands  (considering it is called `~/catkin_ws`): 

0) `cd ~/catkin_ws/src/`
1) `git clone https://github.com/fetchrobotics/fetch_gazebo.git`

Now go back to the workspace and compile it:

2) `cd ~/catkin_ws`
3) `catkin_make`
4) `source devel/setup.bash`

#### 3.4) Launch the simulator
`roslaunch fetch_gazebo simulation.launch`

It may take a while to initiate the gazebo when opening it for the first time, as it downloads the model from internet.
#### 3.5) Check the data
`roslaunch fetch_gazebo playground.launch`
#### 3.6) Open another terminal
`roslaunch fetch_gazebo_demo demo.launch`
#### 3.7) Start rviz and add the depth/image/baselaser to your rviz.
`rviz`

