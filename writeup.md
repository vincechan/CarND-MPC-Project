# Project MPC Controller
Implement a MPC controller in C++ to maneuver the vehicle around the track.

[Link to the video on youtube, car using implemented MPC controller to drive around the track](https://www.youtube.com/watch?v=9sBgUKFiUao)

## The Model 
Describe model in detail. This includes the state, actuators and update equations.


## Timestep Length and Elapsed Duration (N & dt) 
*Student discusses the reasoning behind the chosen N (timestep length) and dt (elapsed duration between timesteps) values. Additionally the student details the previous values tried.*

The combination of N & dt, (N * dt) determines how far in the future the model will predict. The larger the N, the more computation it will be for the solver. The process of coming up with the final value is mainly through trial and error. The intuition is we shouldn't need to predict too far in the future, and we don't want to have N that's too large. Picking N * dt in the 1 to 3 seconds range seems reasonable. I tested (N=30 dt=0.1), (N=20 dt=0.1), (N=10 dt=0.1), (N=20, dt=0.05), (N=10,dt=0.2). (N=10 dt=0.1) resulted in the most table driving with the model. After further experiment, N=12 and dt=0.1 was chosen for the final solution.


## Polynomial Fitting and MPC Preprocessing
*A polynomial is fitted to waypoints. If the student preprocesses waypoints, the vehicle state, and/or actuators prior to the MPC procedure it is described.*



## Model Predictive Control with Latency
The student implements Model Predictive Control that handles a 100 millisecond latency. Student provides details on how they deal with latency.

