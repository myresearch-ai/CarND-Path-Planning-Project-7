# **CarND-Path-Planning-Project-7** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Overview
---

Path planning or path generation is at the core of an autonomous vehicle's design. Being able to safely navigate the environment whether structured or unstructured, involves several considerations ranging from environment perception, localization, sensor fusion, behavior prediction & motion control. To navigate safely, an autonomous vehicle must maintain constant accurate awareness of its environment which involves accurately identifying pedestrians & other static or dynamic objects including other vehicles surrounding the ego vehicle. The goal of this module is to safely navigate the simulated highway having multiple other vehicles with varying behaviors. A successful navigation should stay within legal speed-limit range (50mph), execute legal and safe maneuvers without causing collisions or interferring other vehicles. While navigating the highway, undesired conditions such as *jerk* must be avoided.

Directory Structure
---

```
root
|   CMakeLists.txt
|   cmakepatch.txt
|
|___data
|   |   
|   |   highway_map.csv
|   
|   
|___src
    |   helpers.h
    |   main.cpp
    |   spline.h
    |   json.hpp
    |___Eigen-3.3
        |*
```

Implementation Flow Path (Algorithm)
---

The schematic below provides a visual summary of the anatomy of path planning which consists of prediction, behaviour planning, and trajectory generation.

- **Prediction**: This module or component is responsible for estimating actions other objects (dynamic) might execute in the near-future. Hence if another vehicle is identified, this module will estimate that vehicle's future trajectory.
- **Behavior planning**:This module or component is concerned with  determining the behavior the ego vehicle should exhibit at any point in time such as stopping at a stop light or safely changing lanes to pass a slower vehicle in front of it.
- **Trajectory generation**: This module or component is concerned with generating a safe ego vehicle trajectory based on behavior, predictions & ego vehicle's localization data.

![behavior_planning](https://user-images.githubusercontent.com/76077647/132330621-89d34379-5dde-470b-84af-b258e7c0eb1c.JPG)

The components showed above execute computations at varying frequencies. For successful navigation of the ego vehicle, these computations must be syncronized to achieve smooth, safe, comfortable and legal behavior on the highway. The diagram below shows an example of the compute schedule for the various components of the package.

![scheduling_compute_time](https://user-images.githubusercontent.com/76077647/132337954-b766b04e-41c5-46a8-82e2-150daaa82504.JPG)

Code Style
---

Please (do your best to) stick to [Google's C++ style guide](https://google.github.io/styleguide/cppguide.html).

Dependencies
---

- cmake >= 3.5

    - All OSes: [click here for installation instructions](https://cmake.org/install/)

- make >= 4.1

    - Linux: make is installed by default on most Linux distros
    - Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
    - Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
    
- gcc/g++ >= 5.4

    - Linux: gcc / g++ is installed by default on most Linux distros
    - Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
    - Windows: recommend using [MinGW](http://www.mingw.org/)

- [uWebSockets](https://github.com/uWebSockets/uWebSockets)

    - Run either install-mac.sh or install-ubuntu.sh.
    - If you install from source, checkout to commit e94b6e1, i.e. 
   
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    

Basic Build Instructions
---

1. Clone this repo.
2. Make a build directory: mkdir build && cd build
3. Compile: cmake .. && make
4. Run it: ./path_planning.

References & Credits
---

* udacity (self driving car nanodegree - CarND-Path-Planning-Project)
* course peers
