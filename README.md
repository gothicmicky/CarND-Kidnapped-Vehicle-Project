# Kidnapped Vehicle Project (Particle Filter)

---
## Project Overview
A robot has been kidnapped and transported to a new location! Luckily it has a map of this location, a (noisy) GPS estimate of its initial location, and lots of (noisy) sensor and control data.

In this project a 2 dimensional particle filter in C++ has been implemented. The particle filter is given a map and some initial localization information (analogous to what a GPS would provide). At each time step the filter also gets observation and control data. 

## Dependencies
* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Build Instructions
This project involves the Term 2 Simulator which can be downloaded [here](https://github.com/udacity/self-driving-car-sim/releases)

This repository includes two files that can be used to set up and intall uWebSocketIO for either Linux or Mac systems. For windows you can use either Docker, VMware, or even Windows 10 Bash on Ubuntu to install uWebSocketIO.

Once the install for uWebSocketIO is complete, the main program can be built and ran by doing the following from the project top directory.

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./particle_filter`.

## Particle Filter Implementation

### Particle filter flowchart for this project
![alt text][pf_flowchart]

[pf_flowchart]: ./media/PF_flowchart.png 

### Source Code Structure
The directory structure of this repository is as follows:
```
root
|   CMakeLists.txt
|   README.md
|
|___data
|   |   
|   |   map_data.txt
|   
|___src
    |   helper_functions.h
    |   main.cpp
    |   map.h
    |   particle_filter.cpp
    |   particle_filter.h
```
 `particle_filter.cpp` in the `src` directory contains the scaffolding of a `ParticleFilter` class and some associated methods.
 `src/main.cpp` contains the code that actually run the particle filter and call the associated methods.


### Inputs to the Particle Filter
Sensor input values to the particle filter are provided by the simulator to the c++ program

#### Control Data

// sense noisy position data from the simulator

["sense_x"]

["sense_y"]

["sense_theta"]

// get the previous velocity (in meters per second) and yaw rate (in radians per second) to predict the particle's transitioned state

["previous_velocity"]

["previous_yawrate"]

#### Observation Data

// receive noisy observation data from the simulator, in a respective list of x/y values

["sense_observations_x"]

["sense_observations_y"]

#### The Map*
`map_data.txt` includes the position of landmarks (in meters) on an arbitrary Cartesian coordinate system. Each row has three columns
1. x position
2. y position
3. landmark id

> * Map data provided by 3D Mapping Solutions GmbH.


### Output From the Particle Filter
Output values provided by the c++ program to the simulator.

// best particle values used for calculating the error evaluation

["best_particle_x"]

["best_particle_y"]

["best_particle_theta"] 

### Other Data
//Optional message data used for debugging particle's sensing and associations

// for respective (x,y) sensed positions ID label 

["best_particle_associations"]

// for respective (x,y) sensed positions

["best_particle_sense_x"] <= list of sensed x positions

["best_particle_sense_y"] <= list of sensed y positions


> **NOTE**
> The vehicle's coordinate system is NOT the map coordinate system.
> Transformation (rotation + translation) is required.


## Success Criteria
1. **Accuracy**: your particle filter should localize vehicle position and yaw to within the values specified in the parameters `max_translation_error` and `max_yaw_error` in `src/main.cpp`.

2. **Performance**: the particle filter should complete execution within the time of 100 seconds.


