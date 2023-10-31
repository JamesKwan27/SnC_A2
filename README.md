# Fetch-Robot-Grasping

University of Technology Sydney, Australia.
Assignment for 41014 Sensors and Control for Mechatronic Systems subject, Spring 2023 session

Group Members:
 - James Kwan 13204490  
 - Sagar Rathi 13908722
 - Aidan Sing  14248696  
 
Subject coordinator: Dr. Liang Zhao

Contribution: 
 - James Kwan - 30%
 - Sagar Rathi - 30%
 - Aidan Sing - 40%

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

It may take a while to initiate the gazebo when opening it for the first time, as it downloads the model from internet.
#### 3.5) Open the environment
`roslaunch fetch_gazebo playground.launch`
Wait for the playground.launch to finish initialising before moving on.
#### 3.6) Viewing from the head_camera
`rviz`
Change the fixed frame to `base_link`
Add the /head_camera/depth_downsample/image_raw/Image to your rviz.
#### 3.7) Starting the simulation
`roslaunch fetch_gazebo_demo demo.launch`

### IMPORTANT: Dealing with errors
#### If the demo fails to detect the object due to the fetch robot facing a random side:
Stop the demo using `Ctrl+C` in the terminal where the demo.launch was launched.

Rerun the demo using 3.7):

#### If the arm is extended and fails to grasp the object
Restart all processes within the terminal and redo 3.5) Open the environment, 3.6) Viewing from the head_camera, and 3.7) Starting the simulation.

## 4) Changing the Object Model: ##
Stop the gazebo and rviz simulations using `Ctrl+C` within the repsective terminals.

Navigate to and open `~/catkin_ws/src/fetch_gazebo/fetch_gazebo/worlds/test_zone.sdf`

Edit the object spawned within the environment by replacing `<uri>model://red_cube</uri>` to either:

1) `<uri>model://red_cube</uri>`
2) `<uri>model://red_cylinder</uri>`
3) `<uri>model://red_sphere</uri>`
