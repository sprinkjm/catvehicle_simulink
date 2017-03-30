# catvehicle_simulink
Simulink models used in conjunction with the catvehicle project.

# About
The catvehicle project uses many different kinds of controllers and models, and many of these are best described using domain-specific languages such as Simulink. In this repository, the /source/ models used for those controllers are located.

# How to use this repository
The models in this repository are meant as:
* Principal sources from which code can be directly generated for use with the catvehicle testbed (src/ directory)
* Tutorials that give boilerplate starting positions for your own models (tutorials/ directory)

## src/ models
While you're doing other tutorials in the catvehicle project, you might be asked to export code from existing, ready-to-go models found in this repository. Open up the model, then in another tab
```
roscore
```
Generate the code using Simulink's ```Code->C/C++ Code->Build Model``` (or ```^B```), and then in another tab
```
./build_ros_model.sh modelname.tgz ../path/to/your/workspace
```

## tutorials/ models
Copy the .slx model to your own repository, and make changes to it in order to produce your desired version. Once you have that version, ensure you add it to your own package version control.


# Example tutorial models and their overview

## imageAcquisition.slx
See tutorial at http://cps-vo.org/node/32697

## laserscan2image.slx
See tutorial at http://cps-vo.org/node/34057

## laserscan2templateMatchPolygon.slx
This tutorial builds on the laserscan2image model above, but uses template 
matching (of a PNG screenshot of an interesting object) as a means of 
generating the points in an image where the template is found. The second 
half of the model transforms that pixel location into (x,y) coordinates, 
and then updates a PolygonStamped message based on those pixels, which 
is published to the /detections topic.

## uCanDoIt.slx
This model generates a message on the topic /doIt (do it) which is of kind 
std_msgs/Bool. The value on /doIt should be:
  * false if the vehicle has not moved yet
  * false if the vehicle is moving
  * true if the vehicle has moved since startup, but is stopped now
The state chart "Chart" keeps track of system state, based on the value of 
/catvehicle/vel which is the velocity of the car. 
