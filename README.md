# Review of Visual SLAM

### 1. What is SLAM
SLAM (simultaneous localization and mapping) is a method used for autonomous vehicles that lets you build a map and localize your vehicle in that map at the same time. SLAM algorithms allow the vehicle to map out unknown environments. Engineers use the map information  to carry out tasks such as path planning and obstacle avoidance.

Sensor datas (IMU,camera,Lidar, Camera)->building environement map and estimate pose 

The problems that SLAM solves are Localization and map building under unknown environemnt

### 2. Visual SLAM framwork


   ![image](https://user-images.githubusercontent.com/63558665/119078880-0ba52400-b9c5-11eb-8dc3-0b0b6e667dfd.png)

steps:
* Reading sensors data: reading images and images preprocessing,other sensoe information: IMU and wheel speed sensor
* Front-end: estimating the pose of camera between sequence frames and build local map
* Back-end: Back end receive estimated camera pose at different time step and the information from loop closure detection. optimize these information to build global map based multiple optimization methods: linear(EKF) and non-linear (BA) and to minimize the influence of accumulating drift( error from previous convert to next state, caused by the pose calculated by current state and previous state)
* Loop closure detection:Loop closure detection is the process of detecting whether an agent has returned to a previously visited location.
* Mapping: build map

Accumulating drift: loop closure detection and back end optimization

The most import sensors in Visual SLAM is camera.
1. Monocular camera: single image frame, lose depth information, scale ambiguity
2. Stereo camera: high computation/complicated calibration, measure depth range depends on the baseline
3. RGBD camera: sending infrared strcture light to measure the distance,sensitive to lighting condition，used in indoor environment，ｃannot measure transparent surface．

### 3. Rigid bady transformation in three-dimension space: Rotation matrix, Transformation Matrix,Applications of Quaternions,Axis-angle
#### linear algebra review:
* point
   ![image](https://user-images.githubusercontent.com/63558665/119247009-4ab5af80-bb54-11eb-9026-a89b554d368a.png)
* vector
   ![image](https://user-images.githubusercontent.com/63558665/119247018-5b662580-bb54-11eb-9170-cf675f2f8d23.png)
* Dot product
   ![image](https://user-images.githubusercontent.com/63558665/119247166-653c5880-bb55-11eb-9e82-80fa5fda0fb6.png)
* cross product
   ![image](https://user-images.githubusercontent.com/63558665/119247161-59509680-bb55-11eb-8249-a38f5920e270.png)
   ![image](https://user-images.githubusercontent.com/63558665/119247173-77b69200-bb55-11eb-8b1a-28b0d3a63ff5.png)
   ![image](https://user-images.githubusercontent.com/63558665/119247184-8ef57f80-bb55-11eb-91a2-7a357a9c96df.png)
#### transformation
* Euclidean transformation:
   ![image](https://user-images.githubusercontent.com/63558665/119247262-01665f80-bb56-11eb-9ece-2203b25bd712.png)
   ![image](https://user-images.githubusercontent.com/63558665/119247277-1fcc5b00-bb56-11eb-8af1-7aa9047bee27.png)
The relationship between two coordinations can be expressed as:
   ![image](https://user-images.githubusercontent.com/63558665/119247299-4db19f80-bb56-11eb-8a01-31f1f6d8e6b1.png)
Rotation matrix is orthonormal matrix,Each column(row) vector is a unit vector, They are orthogonal to each other
   ![image](https://user-images.githubusercontent.com/63558665/119247352-b436bd80-bb56-11eb-89d9-d8a35a289312.png)
Since Rotation matrix is orthonomal matrix, then:
   ![image](https://user-images.githubusercontent.com/63558665/119247387-ee07c400-bb56-11eb-8440-445a68b0097f.png)
Considering translation:
   ![image](https://user-images.githubusercontent.com/63558665/119247438-63739480-bb57-11eb-8f21-0af9b6c7552b.png)






