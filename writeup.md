# Project MPC Controller
Implement a MPC controller in C++ to maneuver the vehicle around the track.

[Link to the video on youtube, car using implemented MPC controller to drive around the track](https://www.youtube.com/watch?v=9sBgUKFiUao)

## The Model 
Describe model in detail. This includes the state, actuators and update equations.


## Timestep Length and Elapsed Duration (N & dt) 
Student discusses the reasoning behind the chosen N (timestep length) and dt (elapsed duration between timesteps) values. Additionally the student details the previous values tried.

## Polynomial Fitting and MPC Preprocessing
A polynomial is fitted to waypoints.
If the student preprocesses waypoints, the vehicle state, and/or actuators prior to the MPC procedure it is described.

## Model Predictive Control with Latency
The student implements Model Predictive Control that handles a 100 millisecond latency. Student provides details on how they deal with latency.
