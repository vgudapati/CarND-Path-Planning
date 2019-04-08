# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program
   
### Simulator.
You can download the Term3 Simulator which contains the Path Planning Project from the [releases tab (https://github.com/udacity/self-driving-car-sim/releases/tag/T3_v1.2).  

To run the simulator on Mac/Linux, first make the binary file executable with the following command:
```shell
sudo chmod u+x {simulator_file_name}
```

### Goals
In this project your goal is to safely navigate around a virtual highway with other traffic that is driving +-10 MPH of the 50 MPH speed limit. You will be provided the car's localization and sensor fusion data, there is also a sparse map list of waypoints around the highway. The car should try to go as close as possible to the 50 MPH speed limit, which means passing slower traffic when possible, note that other cars will try to change lanes too. The car should avoid hitting other cars at all cost as well as driving inside of the marked road lanes at all times, unless going from one lane to another. The car should be able to make one complete loop around the 6946m highway. Since the car is trying to go 50 MPH, it should take a little over 5 minutes to complete 1 loop. Also the car should not experience total acceleration over 10 m/s^2 and jerk that is greater than 10 m/s^3.

#### The map of the highway is in data/highway_map.txt
Each waypoint in the list contains  [x,y,s,dx,dy] values. x and y are the waypoint's map coordinate position, the s value is the distance along the road to get to that waypoint in meters, the dx and dy values define the unit normal vector pointing outward of the highway loop.

The highway's waypoints loop around so the frenet s value, distance along the road, goes from 0 to 6945.554.

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./path_planning`.

Here is the data provided from the Simulator to the C++ Program

#### Main car's localization Data (No Noise)

["x"] The car's x position in map coordinates

["y"] The car's y position in map coordinates

["s"] The car's s position in frenet coordinates

["d"] The car's d position in frenet coordinates

["yaw"] The car's yaw angle in the map

["speed"] The car's speed in MPH

#### Previous path data given to the Planner

//Note: Return the previous list but with processed points removed, can be a nice tool to show how far along
the path has processed since last time. 

["previous_path_x"] The previous list of x points previously given to the simulator

["previous_path_y"] The previous list of y points previously given to the simulator

#### Previous path's end s and d values 

["end_path_s"] The previous list's last point's frenet s value

["end_path_d"] The previous list's last point's frenet d value

#### Sensor Fusion Data, a list of all other car's attributes on the same side of the road. (No Noise)

["sensor_fusion"] A 2d vector of cars and then that car's [car's unique ID, car's x position in map coordinates, car's y position in map coordinates, car's x velocity in m/s, car's y velocity in m/s, car's s position in frenet coordinates, car's d position in frenet coordinates. 

## Details

1. The car uses a perfect controller and will visit every (x,y) point it recieves in the list every .02 seconds. The units for the (x,y) points are in meters and the spacing of the points determines the speed of the car. The vector going from a point to the next point in the list dictates the angle of the car. Acceleration both in the tangential and normal directions is measured along with the jerk, the rate of change of total Acceleration. The (x,y) point paths that the planner recieves should not have a total acceleration that goes over 10 m/s^2, also the jerk should not go over 50 m/s^3. (NOTE: As this is BETA, these requirements might change. Also currently jerk is over a .02 second interval, it would probably be better to average total acceleration over 1 second and measure jerk from that.

2. There will be some latency between the simulator running and the path planner returning a path, with optimized code usually its not very long maybe just 1-3 time steps. During this delay the simulator will continue using points that it was last given, because of this its a good idea to store the last points you have used so you can have a smooth transition. previous_path_x, and previous_path_y can be helpful for this transition since they show the last points given to the simulator controller with the processed points already removed. You would either return a path that extends this previous path or make sure to create a new path that has a smooth transition with this last path.

## Tips

A really helpful resource for doing this project and creating smooth trajectories was using http://kluge.in-chemnitz.de/opensource/spline/, the spline function is in a single hearder file is really easy to use.

---

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
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `install-mac.sh` or `install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```

## Editor Settings

We've purposefully kept editor configuration files out of this repo in order to
keep it as simple and environment agnostic as possible. However, we recommend
using the following settings:

* indent using spaces
* set tab width to 2 spaces (keeps the matrices in source code aligned)

## Code Style

Please (do your best to) stick to [Google's C++ style guide](https://google.github.io/styleguide/cppguide.html).

## Project Instructions and Rubric

Note: regardless of the changes you make, your project must be buildable using
cmake and make!


## Call for IDE Profiles Pull Requests

Help your fellow students!

We decided to create Makefiles with cmake to keep this project as platform
agnostic as possible. Similarly, we omitted IDE profiles in order to ensure
that students don't feel pressured to use one IDE or another.

However! I'd love to help people get up and running with their IDEs of choice.
If you've created a profile for an IDE that you think other students would
appreciate, we'd love to have you add the requisite profile files and
instructions to ide_profiles/. For example if you wanted to add a VS Code
profile, you'd add:

* /ide_profiles/vscode/.vscode
* /ide_profiles/vscode/README.md

The README should explain what the profile does, how to take advantage of it,
and how to install it.

Frankly, I've never been involved in a project with multiple IDE profiles
before. I believe the best way to handle this would be to keep them out of the
repo root to avoid clutter. My expectation is that most profiles will include
instructions to copy files to a new location to get picked up by the IDE, but
that's just a guess.

One last note here: regardless of the IDE used, every submitted project must
still be compilable with cmake and make./

## How to write a README
A well written README file can enhance your project and portfolio.  Develop your abilities to create professional README files by completing [this free course](https://www.udacity.com/course/writing-readmes--ud777).

## Reflection

The solution is very closely modeled based on the explanation provided in the [Project Q & A](https://classroom.udacity.com/nanodegrees/nd013/parts/6047fe34-d93c-4f50-8336-b70ef10cb4b2/modules/27800789-bc8e-4adc-afe0-ec781e82ceae/lessons/23add5c6-7004-47ad-b169-49a5d7b1c1cb/concepts/3bdfeb8c-8dd6-49a7-9d08-beff6703792d) video. As discussed in the video, we are using the spline library for interpolating the points to generate the path needed. 

* Start in the middle lane (lane = 1) [line 58](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L58)
* Start with a reference velocity of 0.0 [line 61](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L61)
* Based on the localization and sensor fusion data we need to find the reference velocity(ref_v) to use.
* During the path planning we will be using the points from the previous path and calculate the number of points that we traversed from the previous path.


* First up we check if any lane changes needs to happen depending upon cars current location and surroundings and speed. Contemplate lane changes and take action. 
* Using sensor fusion data, we identify if there is a car in other lanes. [lines 120-130](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L120)
* Once we know which lane other cars and based on the lane we are in, we determine if any other car is in the vicinity of our car. [lines 140-151](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L140)
  * If there is antoher car in front of our car and our car is in one of the right lanes, we attempt to change to one of the left lanes. [lines 192-197](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L192)
  * If there is antoher car in front of our car and our car is in one of the left lanes, we attempt to change to one of the right lanes. [lines 199-201](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L199)
  * If there is antoher car in front of our car and a lane change is not possible, we simply reduce speed. [line 203](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L203)
  * If there is not another car in front of our car, we attpemt to maintain the speed almost up to the speed limit (49.5 here). [lines 213-215](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L213)
  * Once i implemented the above procedure and tested, i found a couple of problems.
    * When the car is changing two lanes at a time, there is too much jerk.
    * Also, the scope for accident was higher in such instances.
  * To address the above two issues, i have implemented code to maintain the car in the middle lane when the surroundings permit. This mostly solved both the issues mentioned above. [lines 207-211](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L207)
* Create a list of widely spaced (x, y) waypoints, evenly spaced at 30m
* Later we will interpolate these waypoints with a spline and fill it in with more points that control speed
* Define reference x, y, yaw states
* If the previous size is almost empty, use the car as starting reference
  * Use two points that make the path tangent to the car and push these points to the path. [lines 231-242](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L231)
  * Otherwise, the previous path's end point as starting reference and use two points that make the path tangent to the previous path's end point. [lines 245-262](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L245)
  * Once we have the starting reference, we use Frenet to generate additional points that are widely spaced at 30, 60 and 90m depending upon which lane our car is. Subsequently add these points to the path. [lines 264-276](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L264)
  //In Frenet add evenly 30m spaced points ahead of the starting reference
  * Using the points generated we shift car reference angle to 0 degrees. [lines 278-285](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L278)
  * Create a spline. Set (x, y) points to the spline. Define the actual (x, y) points we will use for the planner. [lines 288-296](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L288)
  * Using the points we create the path planner. The rationale for paht planner is to use any of the points left from the previous path. [lines 304-308](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L304)
  * Then fill up the rest of out path planner after filling it with previous points, here we will always output 50 points. Also, rotate back to normal after rotating it earlier. [lines 318-338](https://github.com/vgudapati/CarND-Path-Planning/blob/master/src/main.cpp#L318)
  
  


