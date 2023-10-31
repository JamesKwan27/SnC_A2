# Fetch-Robot-Grasping

University of Technology Sydney, Australia.
Assignment for 41014 Sensors and Control for Mechatronic Systems subject, Spring 2023 session

Group Members:
 - James Kwan
 - Sagar Rathi
 - Aidan Sing
 
Subject coordinator: Dr. Liang Zhao

## 1) Project Description: ##
Control the Fetch robot to grasp the object on the table, e.g. can of coke, box of cookies, using the robotic arm and hand by
using visual servoing method. Depth images and/or RGB images can be used for the visual servoing. The end-effector of the robot arm has been calibrated with the RGB-D camera.

Target: The Fetch robot grasps different interested objects on the table without falling down.

## 2) Installation ##

### 2.0) Ubuntu 18.04 LTS (Bionic Beaver)

The following proceures assume you have Ubuntu 18.04 LTS installed on your machine. Download it from the [releases page](http://releases.ubuntu.com/).
 
### 2.1) ROS Melodic 

We will be using ROS Melodic on Ubuntu 18.04 LTS (Bionic Beaver). Follow the instructions at the [ROS Melodic installation instructions page.](https://wiki.ros.org/melodic/Installation/Ubuntu)

A summary of the commands is showed below:

1) `sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`

2) `sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116`

3) `sudo apt-get update`

4) `sudo apt-get install ros-indigo-desktop-full`

5) `sudo rosdep init`

6) `rosdep update`

7) `echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc`

8) `source ~/.bashrc`

### 3) Fetch Robot

[Official documentation page](https://docs.fetchrobotics.com/).

#### 3.1) Install Gazebo simulator Demo
`sudo apt-get install ros-melodic-fetch-gazebo-demo`

#### 3.2) Install the main package from Fetch Robotics GitHub page

Go to your ROS workspace, and do the following commands  (considering it is called `~/ros_ws`): 

0) `cd ~/ros_ws/src/`
1) `git clone https://github.com/fetchrobotics/fetch_ros`

Make sure you're on the right branch:

2) `cd fetch_ros`
3) `git checkout melodic-devel`

Now go back to the workspace and compile it:

2) `cd ~/ros_ws`
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

### Issues

If you have any issues when compiling, go to `ros_ws` and do:
`rosdep install --from-paths src -r -y`

This will install the dependencies of all packages in the workspace. Extracted from http://wiki.ros.org/rosdep.

### Tips
1) Always run `source ros_ws/devel/setup.bash` before running a launch file, it might help.




### Tutorials that might help
http://wiki.ros.org/pr2_controllers/Tutorials
http://docs.ros.org/kinetic/api/moveit_tutorials/html/doc/move_group_python_interface/move_group_python_interface_tutorial.html
http://docs.ros.org/indigo/api/pr2_moveit_tutorials/html/planning/scripts/doc/move_group_python_interface_tutorial.html
