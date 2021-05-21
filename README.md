# Review of Visual SLAM

### 1) What is SLAM
SLAM (simultaneous localization and mapping) is a method used for autonomous vehicles that lets you build a map and localize your vehicle in that map at the same time. SLAM algorithms allow the vehicle to map out unknown environments. Engineers use the map information  to carry out tasks such as path planning and obstacle avoidance.

Sensor datas (IMU,camera,Lidar, Camera)->building environement map and estimate pose 

The problems that SLAM solves are Localization and map building under unknown environemnt

### 2) Visual SLAM framwork


   ![image](https://user-images.githubusercontent.com/63558665/119078880-0ba52400-b9c5-11eb-8dc3-0b0b6e667dfd.png)

steps:
* Reading sensors data: reading images and images preprocessing,other sensoe information: IMU and wheel speed sensor
* Front-end: estimating the pose of camera between sequence frames and build local map
* Back-end: Back end receive estimated camera pose at different time step and the information from loop closure detection. optimize these information to build global map based multiple optimization methods: linear(EKF) and non-linear (BA)
* Loop closure detection:Loop closure detection is the process of detecting whether an agent has returned to a previously visited location.
* Mapping: build map


The most import sensors in Visual SLAM is camera.

1. Monocular camera: single image frame, lose depth information, scale ambiguity

