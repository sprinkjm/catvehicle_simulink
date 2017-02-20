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

