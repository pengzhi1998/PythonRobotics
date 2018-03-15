<img src="https://github.com/AtsushiSakai/PythonRobotics/raw/master/icon.png?raw=true" align="right" width="300"/>

# PythonRobotics
[![Build Status](https://travis-ci.org/AtsushiSakai/PythonRobotics.svg?branch=master)](https://travis-ci.org/AtsushiSakai/PythonRobotics)

Python codes for robotics algorithm.

# Table of Contents
   * [Requirements](#requirements)
   * [How to use](#how-to-use)
   * [Localization](#localization)
      * [Extended Kalman Filter localization](#extended-kalman-filter-localization)
      * [Unscented Kalman Filter localization](#unscented-kalman-filter-localization)
      * [Particle Filter localization](#particle-filter-localization)
   * [Mapping](#mapping)
      * [Gaussian grid map](#gaussian-grid-map)
      * [Ray casting grid map](#ray-casting-grid-map)
   * [SLAM](#slam)
      * [Iterative Closest Point (ICP) Matching](#iterative-closest-point-icp-matching)
      * [EKF SLAM](#ekf-slam)
   * [Path Planning](#path-planning)
      * [Dynamic Window Approach](#dynamic-window-approach)
      * [Grid based search](#grid-based-search)
         * [Dijkstra algorithm](#dijkstra-algorithm)
         * [A* algorithm](#a-algorithm)
         * [Potential Field algorithm](#potential-field-algorithm)
      * [Model Predictive Trajectory Generator](#model-predictive-trajectory-generator)
         * [Path optimization sample](#path-optimization-sample)
         * [Lookup table generation sample](#lookup-table-generation-sample)
      * [State Lattice Planning](#state-lattice-planning)
         * [Uniform polar sampling](#uniform-polar-sampling)
         * [Biased polar sampling](#biased-polar-sampling)
         * [Lane sampling](#lane-sampling)
      * [Probabilistic Road-Map (PRM) planning](#probabilistic-road-map-prm-planning)
      * [Voronoi Road-Map planning](#voronoi-road-map-planning)
      * [Rapidly-Exploring Random Trees (RRT)](#rapidly-exploring-random-trees-rrt)
         * [Basic RRT](#basic-rrt)
         * [RRT*](#rrt)
         * [RRT with dubins path](#rrt-with-dubins-path)
         * [RRT* with dubins path](#rrt-with-dubins-path-1)
         * [RRT* with reeds-sheep path](#rrt-with-reeds-sheep-path)
         * [Closed Loop RRT*](#closed-loop-rrt)
      * [Cubic spline planning](#cubic-spline-planning)
      * [B-Spline planning](#b-spline-planning)
      * [Bezier path planning](#bezier-path-planning)
      * [Quintic polynomials planning](#quintic-polynomials-planning)
      * [Dubins path planning](#dubins-path-planning)
      * [Reeds Shepp planning](#reeds-shepp-planning)
      * [Optimal Trajectory in a Frenet Frame](#optimal-trajectory-in-a-frenet-frame)
   * [Path tracking](#path-tracking)
      * [Pure pursuit tracking](#pure-pursuit-tracking)
      * [Stanley control](#stanley-control)
      * [Rear wheel feedback control](#rear-wheel-feedback-control)
      * [Linear–quadratic regulator (LQR) steering control](#linearquadratic-regulator-lqr-steering-control)
      * [Linear–quadratic regulator (LQR) speed and steering control](#linearquadratic-regulator-lqr-speed-and-steering-control)
      * [Model predictive speed and steering control](#model-predictive-speed-and-steering-control)
   * [License](#license)
   * [Contribution](#contribution)
   * [Author](#author)

# Requirements

- Python 3.6.x

- numpy

- scipy

- matplotlib

- pandas

- [cvxpy 0.4.x](http://www.cvxpy.org/en/latest/) 

# How to use

1. Install the required libraries.

2. Clone this repo.

3. Execute python script in each directory.

4. Add star to this repo if you like it :smiley:. 

# Localization

## Extended Kalman Filter localization

<img src="https://github.com/AtsushiSakai/PythonRobotics/raw/master/Localization/extended_kalman_filter/animation.gif" width="640">

This is a sensor fusion localization with Extended Kalman Filter(EKF).

The blue line is true trajectory, the black line is dead reckoning trajectory,

the green point is positioning observation (ex. GPS), and the red line is estimated trajectory with EKF.

The red ellipse is estimated covariance ellipse with EKF.

## Unscented Kalman Filter localization

![2](https://github.com/AtsushiSakai/PythonRobotics/raw/master/Localization/unscented_kalman_filter/animation.gif)

This is a sensor fusion localization with Unscented Kalman Filter(UKF).

The lines and points are same meaning of the EKF simulation.

Ref:

- [Discriminatively Trained Unscented Kalman Filter for Mobile Robot Localization](https://www.researchgate.net/publication/267963417_Discriminatively_Trained_Unscented_Kalman_Filter_for_Mobile_Robot_Localization)

## Particle Filter localization

![2](https://github.com/AtsushiSakai/PythonRobotics/raw/master/Localization/particle_filter/animation.gif)

This is a sensor fusion localization with Particle Filter(PF).

The blue line is true trajectory, the black line is dead reckoning trajectory,

and the red line is estimated trajectory with PF.

It is assumed that the robot can measure a distance from landmarks (RFID).

This measurements are used for PF localization.

# Mapping

## Gaussian grid map

This is a 2D gaussian grid mapping example.

![2](https://github.com/AtsushiSakai/PythonRobotics/raw/master/Mapping/gaussian_grid_map/animation.gif)

## Ray casting grid map

This is a 2D ray casting grid mapping example.

![2](https://github.com/AtsushiSakai/PythonRobotics/raw/master/Mapping/raycasting_grid_map/animation.gif)


# SLAM

Simultaneous Localization and Mapping(SLAM) examples

## Iterative Closest Point (ICP) Matching

This is a 2D ICP matching example with singular value decomposition.

It can calculate a rotation matrix and a translation vector between points to points.

![3](https://github.com/AtsushiSakai/PythonRobotics/raw/master/SLAM/iterative_closest_point/animation.gif)

Ref:

- [Introduction to Mobile Robotics: Iterative Closest Point Algorithm](https://cs.gmu.edu/~kosecka/cs685/cs685-icp.pdf)


## EKF SLAM

This is a Extended Kalman Filter based SLAM example.

The blue line is ground truth, the black line is dead reckoning, the red line is the estimated trajectory with EKF SLAM.

The green cross are estimated landmarks.

![3](https://github.com/AtsushiSakai/PythonRobotics/raw/master/SLAM/EKFSLAM/animation.gif)

Ref:

- [PROBABILISTIC ROBOTICS](http://www.probabilistic-robotics.org/)

## Fast SLAM 1.0

This is a feature based SLAM example using FastSLAM 1.0.

The blue line is ground truth, the black line is dead reckoning, the red line is the estimated trajectory with FastSLAM1.0.

The red points are particles of FastSLAM.

Black points are landmarks, Blue crosses are estimated landmark positions by FastSLAM.


![3](https://github.com/AtsushiSakai/PythonRobotics/raw/master/SLAM/FastSLAM1/animation.gif)


Ref:

- [PROBABILISTIC ROBOTICS](http://www.probabilistic-robotics.org/)

- [Matlab Utilities](http://www-personal.acfr.usyd.edu.au/tbailey/software/slam_simulations.htm)


# Path Planning

## Dynamic Window Approach

This is a 2D navigation sample code with Dynamic Window Approach.

- [The Dynamic Window Approach to Collision Avoidance](https://www.ri.cmu.edu/pub_files/pub1/fox_dieter_1997_1/fox_dieter_1997_1.pdf)

![2](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/DynamicWindowApproach/animation.gif)


## Grid based search

### Dijkstra algorithm

This is a 2D grid based shortest path planning with Dijkstra's algorithm.

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/Dijkstra/animation.gif)

In the animation, cyan points are searched nodes.

### A\* algorithm

This is a 2D grid based shortest path planning with A star algorithm.

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/AStar/animation.gif)

In the animation, cyan points are searched nodes.

It's heuristic is 2D Euclid distance.

### Potential Field algorithm

This is a 2D grid based path planning with Potential Field algorithm.

![PotentialField](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/PotentialFieldPlanning/animation.gif)

In the animation, the blue heat map shows potential value on each grid.

Ref:

- [Robotic Motion Planning:Potential Functions](https://www.cs.cmu.edu/~motionplanning/lecture/Chap4-Potential-Field_howie.pdf)


## Model Predictive Trajectory Generator

This is a path optimization sample on model predictive trajectory generator.

This algorithm is used for state lattice planner. 

### Path optimization sample

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/ModelPredictiveTrajectoryGenerator/kn05animation.gif)

### Lookup table generation sample

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/ModelPredictiveTrajectoryGenerator/lookuptable.png?raw=True)

Ref: 

- [Optimal rough terrain trajectory generation for wheeled mobile robots](http://journals.sagepub.com/doi/pdf/10.1177/0278364906075328)


## State Lattice Planning

This script is a path planning code with state lattice planning.

This code uses the model predictive trajectory generator to solve boundary problem.


### Uniform polar sampling

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/StateLatticePlanner/UniformPolarSampling.gif)


### Biased polar sampling

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/StateLatticePlanner/BiasedPolarSampling.gif)


### Lane sampling

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/StateLatticePlanner/LaneSampling.gif)

## Probabilistic Road-Map (PRM) planning 

![PRM](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/ProbabilisticRoadMap/animation.gif)

This PRM planner uses Dijkstra method for graph search.

In the animation, blue points are sampled points,

Cyan crosses means searched points with Dijkstra method,

The red line is the final path of PRM.

Ref:

- [Probabilistic roadmap \- Wikipedia](https://en.wikipedia.org/wiki/Probabilistic_roadmap)

　　
## Voronoi Road-Map planning 

![VRM](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/VoronoiRoadMap/animation.gif)

This Voronoi road-map planner uses Dijkstra method for graph search.

In the animation, blue points are Voronoi points,

Cyan crosses means searched points with Dijkstra method,

The red line is the final path of Vornoi Road-Map.

Ref:

- [Robotic Motion Planning](https://www.cs.cmu.edu/~motionplanning/lecture/Chap5-RoadMap-Methods_howie.pdf)


## Rapidly-Exploring Random Trees (RRT)

### Basic RRT 

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/RRT/animation.gif)

This script is a simple path planning code with Rapidly-Exploring Random Trees (RRT)

Black circles are obstacles, green line is a searched tree, red crosses are start and goal positions.

### RRT\*

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/RRTstar/animation.gif)

This script is a  path planning code with RRT\*

Black circles are obstacles, green line is a searched tree, red crosses are start and goal positions.

Ref:

- [Incremental Sampling-based Algorithms for Optimal Motion Planning](https://arxiv.org/abs/1005.0416)

- [Sampling-based Algorithms for Optimal Motion Planning](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.419.5503&rep=rep1&type=pdf)


### RRT with dubins path 

![PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/RRTDubins/animation.gif)

Path planning for a car robot with RRT and dubins path planner.


### RRT\* with dubins path

![AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/RRTStarDubins/animation.gif)

Path planning for a car robot with RRT\* and dubins path planner.


### RRT\* with reeds-sheep path

![Robotics/animation.gif at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/RRTStarReedsShepp/animation.gif))

Path planning for a car robot with RRT\* and reeds sheep path planner.

### Closed Loop RRT\*

A vehicle model based path planning with closed loop RRT\*.

![CLRRT](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/ClosedLoopRRTStar/animation.gif)

In this code, pure-pursuit algorithm is used for steering control, 

PID is used for speed control.

Ref:

- [Motion Planning in Complex Environments
using Closed-loop Prediction](http://acl.mit.edu/papers/KuwataGNC08.pdf)

- [Real-time Motion Planning with Applications to
Autonomous Urban Driving](http://acl.mit.edu/papers/KuwataTCST09.pdf)

- [[1601.06326] Sampling-based Algorithms for Optimal Motion Planning Using Closed-loop Prediction](https://arxiv.org/abs/1601.06326)

## Cubic spline planning

A sample code for cubic path planning.

This code generates a curvature continuous path based on x-y waypoints with cubic spline.

Heading angle of each point can be also calculated analytically.

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/CubicSpline/Figure_1.png?raw=True)
![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/CubicSpline/Figure_2.png?raw=True)
![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/CubicSpline/Figure_3.png?raw=True)


## B-Spline planning

![B-Spline](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/BSplinePath/Figure_1.png?raw=True)

This is a path planning with B-Spline curse.

If you input waypoints, it generates a smooth path with B-Spline curve.

The final course should be on the first and last waypoints. 

Ref: 

- [B\-spline \- Wikipedia](https://en.wikipedia.org/wiki/B-spline)

## Bezier path planning

A sample code of Bezier path planning.

It is based on 4 control points Beier path.

![Bezier1](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/BezierPath/Figure_1.png?raw=True)

If you change the offset distance from start and end point,

You can get different Beizer course:

![Bezier2](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/BezierPath/Figure_2.png?raw=True)

 
Ref:

- [Continuous Curvature Path Generation Based on Bezier Curves for Autonomous Vehicles](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.294.6438&rep=rep1&type=pdf)

## Quintic polynomials planning

Motion planning with quintic polynomials.

![2](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/QuinticPolynomialsPlanner/animation.gif)

It can calculate 2D path, velocity, and acceleration profile based on quintic polynomials.

Ref:

- [Local Path Planning And Motion Control For Agv In Positioning](http://ieeexplore.ieee.org/document/637936/)


## Dubins path planning

A sample code for Dubins path planning.

![dubins](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/DubinsPath/animation.gif?raw=True)

Ref:

- [Dubins path - Wikipedia](https://en.wikipedia.org/wiki/Dubins_path)

## Reeds Shepp planning

A sample code with Reeds Shepp path planning.

![RSPlanning](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/ReedsSheppPath/animation.gif?raw=true)

Ref:

- [15.3.2 Reeds\-Shepp Curves](http://planning.cs.uiuc.edu/node822.html) 

- [optimal paths for a car that goes both forwards and backwards](https://pdfs.semanticscholar.org/932e/c495b1d0018fd59dee12a0bf74434fac7af4.pdf)

- [ghliu/pyReedsShepp: Implementation of Reeds Shepp curve\.](https://github.com/ghliu/pyReedsShepp)


## Optimal Trajectory in a Frenet Frame 

![3](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathPlanning/FrenetOptimalTrajectory/animation.gif)

This is optimal trajectory generation in a Frenet Frame.

The cyan line is the target course and black crosses are obstacles.

The red line is predicted path.

Ref:

- [Optimal Trajectory Generation for Dynamic Street Scenarios in a Frenet Frame](https://www.researchgate.net/profile/Moritz_Werling/publication/224156269_Optimal_Trajectory_Generation_for_Dynamic_Street_Scenarios_in_a_Frenet_Frame/links/54f749df0cf210398e9277af.pdf)

- [Optimal trajectory generation for dynamic street scenarios in a Frenet Frame](https://www.youtube.com/watch?v=Cj6tAQe7UCY)


# Path tracking

## Pure pursuit tracking

Path tracking simulation with pure pursuit steering control and PID speed control.

![2](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathTracking/pure_pursuit/animation.gif)

The red line is a target course, the green cross means the target point for pure pursuit control, the blue line is the tracking.

Ref:

- [A Survey of Motion Planning and Control Techniques for Self-driving Urban Vehicles](https://arxiv.org/abs/1604.07446)

## Stanley control

Path tracking simulation with Stanley steering control and PID speed control.

![2](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathTracking/stanley_controller/animation.gif)

Ref:

- [Stanley: The robot that won the DARPA grand challenge](http://robots.stanford.edu/papers/thrun.stanley05.pdf)

- [Automatic Steering Methods for Autonomous Automobile Path Tracking](https://www.ri.cmu.edu/pub_files/2009/2/Automatic_Steering_Methods_for_Autonomous_Automobile_Path_Tracking.pdf)



## Rear wheel feedback control

Path tracking simulation with rear wheel feedback steering control and PID speed control.

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathTracking/rear_wheel_feedback/animation.gif)

Ref:

- [A Survey of Motion Planning and Control Techniques for Self-driving Urban Vehicles](https://arxiv.org/abs/1604.07446)


## Linear–quadratic regulator (LQR) steering control

Path tracking simulation with LQR steering control and PID speed control.

![PythonRobotics/figure_1.png at master · AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathTracking/lqr_steer_control/animation.gif)

Ref:

- [ApolloAuto/apollo: An open autonomous driving platform](https://github.com/ApolloAuto/apollo)


## Linear–quadratic regulator (LQR) speed and steering control

Path tracking simulation with LQR speed and steering control.

![3](https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathTracking/lqr_speed_steer_control/animation.gif)

Ref:

- [Towards fully autonomous driving: Systems and algorithms \- IEEE Conference Publication](http://ieeexplore.ieee.org/document/5940562/)


## Model predictive speed and steering control

Path tracking simulation with iterative linear model predictive speed and steering control.

<img src="https://github.com/AtsushiSakai/PythonRobotics/raw/master/PathTracking/model_predictive_speed_and_steer_control/animation.gif" width="640">

This code uses cvxpy as an optimization modeling tool.

- [Welcome to CVXPY](http://www.cvxpy.org/en/latest/)

Ref:

- [Vehicle Dynamics and Control \| Rajesh Rajamani \| Springer](http://www.springer.com/us/book/9781461414322)

- [MPC Course Material \- MPC Lab @ UC\-Berkeley](http://www.mpc.berkeley.edu/mpc-course-material)

 

# License 

MIT

# Contribution

If you have any quesions or problems about this code, feel free to add an issue.

A small PR like bug fix is welcome.

# Author

Atsushi Sakai ([@Atsushi_twi](https://twitter.com/Atsushi_twi))








