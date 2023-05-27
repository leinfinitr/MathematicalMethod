# Convex Optimization Report

## Author

* Name: Jialong Liu
* SID: 518010910009

## Problem

Given robot state $x_t \in R^2$ and control inputs $u_t \in R^2$ . The objective is
$$minimize \sum_{t=0}^{T-1} || x_t-x_{t+1}||_2^2 + ||u_t||_2^2$$
The robot starts from point (0.1, 5) and wants to reach the point (0, -5). The moving
speed in the X direction shall not exceed 1, and the moving speed in the Y direction
shall not exceed 1. The value of T shall not exceed 15. The dynamics of the system is
$$x_{t+1} = x_t + u_t$$
The robot cannot collide with obstacles (when the robot is on the boundary of the
obstacle, we think there is no collision).

## condition 1

***There is no obstacle***

We just need to change limits of given code to solve this problem.

* state dimension: n = 2
* input dimension: m = 2
* time horizon: T = 15
* state transition matrix: A = I
* input matrix: B = I
* start state: x_0 = [0.1, 5]
* target state: x_T = [0, -5]

The trajectory of the robot in a coordinate system is shown in the following figure.

<center>
    <img src="./answer1.jpg" width = 300 height = 200>
    <img src="./trajectory1.jpg" width = 300 height = 200>
</center>

## condition 2

***There is a circular obstacle at point (0, 0) and its radius is 2***

We can divide the constraint into two parts. 

* For first seven steps, add a constraint that every point should be above the tangent of the circle and start point
$$- \frac{\sqrt{21}}{2} x - y + 5 = 0$$
* For the rest steps, add a constraint that every point should be below the tangent of the circle and end point
$$\frac{\sqrt{21}}{2} x - y - 5 = 0$$

The trajectory of the robot in a coordinate system is shown in the following figure.

<center>
    <img src="./answer2.jpg" width = 300 height = 200>
    <img src="./trajectory2.jpg" width = 300 height = 200>
</center>

## condition 3

***There is a circular obstacle at point (1, 1) and its radius is 1 and a circular obstacle at point (-0.9, -1) and its radius is 1***

We can divide the constraint into five parts. 

* For steps 1 to 5 , no additional constraints are added
* For steps 6 , add a constraint that the point should be left of line $x = 0$
* For step 7 to 8 , no additional constraints are added
* For steps 9 , add a constraint that the point should be right of line $x = 0.1$
* For step 10 to 15 , no additional constraints are added

The trajectory of the robot in a coordinate system is shown in the following figure.

<center>
    <img src="./answer3.jpg" width = 300 height = 200>
    <img src="./trajectory3.jpg" width = 300 height = 200>
</center>
