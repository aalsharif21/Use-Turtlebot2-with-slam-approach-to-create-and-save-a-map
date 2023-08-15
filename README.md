# Use Turtlebot3 with SLAM approach to create and save a map
![picture](Simulation.GIF)

## 1-Download-and-Install-Ubuntu-on-PC:
### 1.1 Download the proper `Ubuntu 20.04 LTS Desktop` image for your PC from the links below.
* [Ubuntu 20.04 LTS Desktop image (64-bit)](https://releases.ubuntu.com/20.04/)
### 1.2 Follow the instruction below to install Ubuntu on PC:
* [Install Ubuntu desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)
 <br/>

## 2-Install-ROS-on-Remote-PC:
Open the terminal with `Ctrl` + `Alt` + `T` and enter below commands one at a time.<br/>
In order to check the details of the easy installation script.<br/>
`$ sudo apt update` <br/>
`$ sudo apt upgrade` <br/>
`$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh` <br/>
`$ chmod 755 ./install_ros_noetic.sh`<br/>
`$ bash ./install_ros_noetic.sh`<br/>
<br/>

## 3-Install-Dependent-ROS-Packages:
`$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \`<br/>
  `ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \`<br/>
  `ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \`<br/>
  `ros-noetic-rosserial-python ros-noetic-rosserial-client \`<br/>
  `ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \`<br/>
  `ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \`<br/>
  `ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \`<br/>
  `ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-marker`<br/>
<br/>  

## 4-Install-TurtleBot3-Packages:
Install TurtleBot3 via Debian Packages.<br/>
`$ sudo apt install ros-noetic-dynamixel-sdk`<br/>
`$ sudo apt install ros-noetic-turtlebot3-msgs`<br/>
`$ sudo apt install ros-noetic-turtlebot3`<br/>
<br/>

## 5-Gazebo-Simulation:
### 5.1 Install Simulation Package:
The <b>TurtleBot3 Simulation Package</b> requires `turtlebot3` and `turtlebot3_msgs` packages as prerequisite. Without these prerequisite packages, the Simulation cannot be launched.<br/>
Please follow the [PC Setup](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/) instructions if you did not install required packages and dependent packages<br/>

`$ cd ~/catkin_ws/src/` <br/>
`$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git`<br/>
`$ cd ~/catkin_ws && catkin_make`<br/>

### 5.2 Launch Simulation World:
Three simulation environments are prepared for TurtleBot3. Please select one of these environments to launch Gazebo.

<b>`Please make sure to completely terminate other Simulation world before launching a new world.`</b> <br/>
<b> TurtleBot3 World </b> <br/>

`$ export TURTLEBOT3_MODEL=waffle`<br/>
`$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`<br/>
<br/>
![picture](s1.jpg)


## 6-SLAM-Simulation:
### 6.1 Run SLAM Node:
Open a new terminal from Remote PC with `Ctrl` + `Alt` + `T` and run the SLAM node. Gmapping SLAM method is used by default.<br/>
Please use the proper keyword among `burger` , `waffle` , `waffle_pi` for the TURTLEBOT3_MODEL parameter.<br/>

`$ export TURTLEBOT3_MODEL=burger`<br/>
`$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping`<br/>
<br/>

![picture](s2.jpg)

### 6.2 Run Teleoperation Node:
Open a new terminal from Remote PC with `Ctrl` + `Alt` + `T` and run the teleoperation node from the Remote PC.<br/><br/>
Please use the proper keyword among `burger` , `waffle` , `waffle_pi` for the TURTLEBOT3_MODEL parameter.<br/>

`$ export TURTLEBOT3_MODEL=burger`<br/>
`$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`<br/>
<br/>

![picture](s3.jpg)

### 6.3 Save Map:
When the map is created successfully, open a new terminal from Remote PC with `Ctrl` + `Alt` + `T` and save the map. <br/>
<br/>

![picture](s4.jpg)

`$ rosrun map_server map_saver -f ~/map` <br/>
<br/>



## 7-Testing:
![picture](testing.GIF)


