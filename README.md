# Arduino-Robot-Arm-Installation-on-ROS-Melodic
 Installing and configuring robot arm package on ROS Melodic 

## Description

After installing ROS in Ubuntu you need these steps to install arm package

* Ubuntu version: 18.4

* ROS version: Melodic


### Create a workspase with Catkin
```
 source /opt/ros/melodic/setup.bash
 mkdir -p ~/catkin_ws/src
 cd ~/catkin_ws/ 
 catkin_make
 source devel/setup.bash
```
Now your ROS workspace is ready to have packages installed in it


### Installing Arduino Robot Arm Package
1. These commands will add the ardunino robot arm package to the src folder
```
 cd ~/catkin_ws/src/
 sudo apt install git
 git clone https://github.com/smart-methods/arduino_robot_arm
```


2. These commands will install all the necessary dependencies
```
 cd ~/catkin_ws
 rosdep install --from-paths src --ignore-src -r -y
 sudo apt-get install ros-melodic-moveit
 sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
 sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
 sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
```

3. This final command will compile all packages in your src folder
```
 catkin_make
```


4.Go to bashrc folder and do the following 
on terminal
```
gedit ~/.bashrc
```

It will open file at the end of the file add the follwing line:

```
source /home/**username**/catkin_ws/devel/setup.bash
```
![Screenshot from 2023-07-17 17-06-08](https://github.com/ya77ya/Arduino-Robot-Arm-Installation-on-ROS/assets/90250848/7add282c-549f-41b8-8969-005a43931490)

make sure to switche **username** with your local username


After that save it and back to terminal and type 

```
source ~/.bashrc
```
 


## Configuring Arduino with ROS
1. Install [Arduino IDE](https://www.arduino.cc/en/software) in Ubuntu 
2. After unzipping the folder run the command `$ sudo ./install.sh`
3. Launch the Arduino IDE
4. Install the arduino package and ros library

![Screenshot from 2022-08-31 10-57-25](https://github.com/ya77ya/Arduino-Robot-Arm-Installation-on-ROS-Melodic/blob/main/Configuring%20Arduino.png)



## Simulation
### Controlling the robot arm by joint_state_publisher
```
roslaunch robot_arm_pkg check_motors.launch
```

![joint_state_publisher](https://github.com/ya77ya/Arduino-Robot-Arm-Installation-on-ROS-Melodic/blob/main/joint_state_publisher.png)

![joint_state_publisher](https://github.com/ya77ya/Arduino-Robot-Arm-Installation-on-ROS-Melodic/blob/main/joint_state_publisher.gif)

You can also connect with hardware by running
```
rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```

## Controlling the robot arm by  gazebo
```
roslaunch robot_arm_pkg check_motors_gazebo.launch
```

![Gazebo](https://github.com/ya77ya/Arduino-Robot-Arm-Installation-on-ROS-Melodic/blob/main/Gazebo.png)

![Gazebo](https://github.com/ya77ya/Arduino-Robot-Arm-Installation-on-ROS-Melodic/blob/main/Gazebo.gif)


You can also connect with hardware by running
```
rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```


## Controlling the robot arm by movelet
```
roslaunch moveit_pkg demo.launch
```

![movelet](https://github.com/ya77ya/Arduino-Robot-Arm-Installation-on-ROS-Melodic/blob/main/movelet.png)

![movelet](https://github.com/ya77ya/Arduino-Robot-Arm-Installation-on-ROS-Melodic/blob/main/movelet.gif)


You can also connect with hardware by running
```
rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```
