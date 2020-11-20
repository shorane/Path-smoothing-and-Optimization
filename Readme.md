# Path smoothing and Trajectory Optimization

This page is created to demonstrate the intermediate results of an ongoing project in path smoothing and optimization.
Due to potential novelty in the code, it has not been made available yet, but will be uploaded in the future.

## What the algorithm does: 
The algorithm generates smooth collision-free paths with C1 continuity for autonomous agents with non-holonomic constraints.

Corridor enviroment |  Maze environment  | Scattered environment
:-------------------------:|:-------------------------:|:-------------------------:
<img src="https://github.com/shorane/Path-smoothing-and-Optimization/blob/master/results/Corridor.png" height="250" />  | <img src="https://github.com/shorane/Path-smoothing-and-Optimization/blob/master/results/Maze.png" height="250" />  | <img src="https://github.com/shorane/Path-smoothing-and-Optimization/blob/master/results/Scatter.png" height="250" />

## How it is done: 
- This is a post-processing algorithm that works on the initial path generated by the Rapidly Exploring Random Trees (RRT) algorithm.
- The implementation uses Dubins curves as the extend/steer function.
- The RRT-Dubins combination helps ensure C1 continuity while generating an initial start to goal path quickly.
- The post-processing function optimizes this initial path for curvature and path length.
- There are two different levels of optimization based on the requirements of application.

The below illustrations show how the post-processing function optimizes the initial loopy and sub-par path and generates a much smoother and shorter path.

Corridor enviroment |  Maze environment  | Scattered environment
:-------------------------:|:-------------------------:|:-------------------------:
<img src="https://github.com/shorane/Path-smoothing-and-Optimization/blob/master/results/def.gif" height="250" />  | <img src="https://github.com/shorane/Path-smoothing-and-Optimization/blob/master/results/maze-cropped.gif" height="250" />  | <img src="https://github.com/shorane/Path-smoothing-and-Optimization/blob/master/results/scatter.gif" height="250" />

## Result:
- The final path is much smoother and is close to the asymptotically optimal paths generated by the RRT* algorithm. 
- The added bonus is that this algorithm is much faster than RRT*, and can be potentially deployed in an anytime fashion. 

The below results show the comparison of path charateristics of the base path against 2 different levels of optimization applied by the post processing algorithm. The results have been averaged after running 100 iterations of each version in three different test environments.

<img src = "https://github.com/shorane/Path-smoothing-and-Optimization/blob/master/results/Optimization-of-RRT-algorithm%20(2).jpg" height="400"/>

## Benchmarking: [(benchmarking report)](https://github.com/shorane/Path-smoothing-and-Optimization/blob/master/results/benchmarking/Benchmarking_Report.pdf)
The developed RRT-Dubins-Post_Processing algorithm has been benchmarked against other common methods like the following:
- RRT with Bezier curves [(Source)](https://github.com/arpitkalla/bezier-rrt)
- SST (Stable Sparse RRT) [(Source)](https://github.com/krishauser/pyOptimalMotionPlanning)
- RRT with POSQ controller as an extend function [(Source)](https://github.com/palmieri/posq) [(Paper)](https://ieeexplore.ieee.org/document/6942562/similar#similar)

### Metrics for comparison:
- Average curvature
- Number of curvature peaks
- Maximum curvature
- Average curvature variation
- Number of curvature variation peaks
- Path length

The Benchmarking report can be found here: [Link to benchmarking report](https://github.com/shorane/Path-smoothing-and-Optimization/blob/master/results/benchmarking/Benchmarking_Report.pdf)





To view more relevant projects: 
- visit my portfolio website [here](https://horaneshubham.wixsite.com/autonomous)
- view my other repositories on [GitHub](https://github.com/shorane)
- connect with me via [LinkedIn](https://www.linkedin.com/in/shubham-horane/)
- email me at shorane@clemson.edu
