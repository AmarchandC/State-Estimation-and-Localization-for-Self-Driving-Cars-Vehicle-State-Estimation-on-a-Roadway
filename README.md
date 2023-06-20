![math](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/368a50c7-ee37-4b32-8d16-9318dc5c9ccc)# State Estimation and Localization for Self Driving Cars: Vehicle State Estimation on a Roadway (Project Report)
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


Vehicle State: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/d5aced71-aa74-4303-b76a-d822f8553ce1)

IMU Measurements: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/c5e2b860-384a-4861-a19d-8ce21790efff)

**2. Prediction**
**Motion Model**
Vehicle's predicted states using the motion model would be as follows:

Predicted State: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/1bf01117-c499-41ee-b4b7-8944c63b534a)|


Predicted Position: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/eb129568-ac70-4dd3-8d10-8432c1bb2412) |


Predicted Velocity: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/6f41752f-07b4-4142-bd70-8f3bd520fa8a)|


Predicted Orientation: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/03826944-5fb2-464a-bf92-f2c835527ad1)|

**Error State Linearization**

In the error-state Kalman filter,th rather than applying the filter to the while nominal stae, the filter will be applied only to the error state.

The error states will be first estimated and then it will be used to correct the nominal state.

The linearized error dynamics is used now to get the error states.

Error State: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/3988f651-60a6-45b3-9fa2-8f2772a60ed5)

Error Dynamics: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/b52ee675-e484-47c6-a388-e23cb5cf0624)

Measurement Noise: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/48a6409c-48f8-4dde-b140-45b001317b9b)

Where, 

![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/82d3dcad-3abe-4c7a-ac4c-6eb5007a037c) is the motion model jacobian,

![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/3c285c0b-4277-4cb7-aa7d-6c9df12d3775) is the Motion Model Noise Jacobian, and


![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/5a97f89f-1872-4999-b163-b5c03520f96e) is the IMU Noise Covariance


**Uncertainity Propagation**

The Jacobian Matrices computed will be used to propagate the uncertainities forward in time. Uncertainity is captured by state covariance matrix. Untill we obtain a measurement, the uncertainity grows.


Predicted State Covariance: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/05016ccf-b0ad-4f2e-83df-365cab7a539d)

**3.Correction Stage**

**Measurement Model**


Measurement Model: ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/b69b73cb-6988-4ae8-a106-a3736ab86a26)


Measurement Noise (GNSS): ![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/278348a2-9728-4bd6-ade0-9e361fe52a88)


LIDAR Measurement Noise:![image](https://github.com/AmarchandC/State-Estimation-and-Localization-for-Self-Driving-Cars-Vehicle-State-Estimation-on-a-Roadway/assets/82858194/51694121-4634-44a4-8924-d52f9e1d9978)

**Measurement Updte**
