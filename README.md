# State Estimation and Localization for Self Driving Cars: Vehicle State Estimation on a Roadway (Project Report)
The final project in the second course in the Self Driving Car specialization offered by Coursera.

**Objective:** This project aims to implement an Error-State Extended Kalman Filter (ES-EKF) for vehicle localization using the data from the CARLA simulator. 

**Introduction:** State estimation using the Kalman filter is a powerful technique used in various fields, such as control systems, robotics, and signal processing. It provides a mathematical framework to estimate the true state of a system by fusing noisy measurements with system dynamics. By utilizing a recursive algorithm, the Kalman filter optimally combines the current state estimate with new measurements to generate an improved estimate in a real-time fashion. It effectively handles uncertainties and can handle both linear and nonlinear systems. With its wide applicability, the Kalman filter has become a cornerstone of modern estimation and control theory.

![p2_1](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/e3c4672b-bd26-4372-9974-f9b4cf68e555)


The Kalman Filter algorithm updates a state estimate through two stages:
1. Prediction using the motion model
2. Correction using the measurement model

**Methodology**

**1. Vehicle State Initialization**

The vehicle state comprises position, velocity, and orientation, which is parameterized by a unit quaternion. The motion model relies on inputs derived from the measurements of specific force (acceleration) and angular rate obtained from the Inertial Measurement Unit (IMU). By incorporating these IMU measurements into the Kalman filter, it becomes possible to accurately estimate the dynamic state of the vehicle. This estimation process takes into account the noise and uncertainties inherent in the IMU measurements, resulting in reliable and precise estimates of the vehicle's motion parameters.

|  Description    |   Equation    |
| -------------   | ------------- |
| Vehicle State   |![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/d5aced71-aa74-4303-b76a-d822f8553ce1)|
| | |
| IMU Measurements|![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/c5e2b860-384a-4861-a19d-8ce21790efff)|

**2. Prediction**

Vehicle's predicted states using the motion model would be as follows:

Predicted State: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/1bf01117-c499-41ee-b4b7-8944c63b534a)|


Predicted Position: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/eb129568-ac70-4dd3-8d10-8432c1bb2412) |


Predicted Velocity: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/6f41752f-07b4-4142-bd70-8f3bd520fa8a)|


Predicted Orientation: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/03826944-5fb2-464a-bf92-f2c835527ad1)|




   
