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

The waypoints are given in the map's coordinate system. The solution would substract the waypoints x coordinates by current x coordinate, and waypoints y coordinates by current y coordinate. As a result, the vechile x and y coordinates will be at zero. The solution also rotate psi by 90 degrees, so instead of getting verticle line, we will have a horizontal line. The preprocessing helps simply the polynomial fit as well as the equations to calcuate cte and epsi.


## Model Predictive Control with Latency
The student implements Model Predictive Control that handles a 100 millisecond latency. Student provides details on how they deal with latency.

With 100 milliseconds, if the car is driving at 50mph (22.35m/s), the car will be off by 2.24meters by the time the actuators effect are applied. The higher the speed, the more the model will be off.

I found that if the cost terms for the cte and epsi are strong enough, the model is good enough to drive around the track if we lower the reference speed. In this solution, I used another approach. I updated the initial state to account for this 100ms delay. Using the current px, py, psi, and speed, I estimate where the vehicle would be after 100ms using the kinematic model equations:

new_px = px + cos(psi) * speed * delta_time;

new_py = py + sin(psi) * speed * delta_time;

With this approach, the solution was able to achieved max speed of ~90m/h on the track with the delay. 

