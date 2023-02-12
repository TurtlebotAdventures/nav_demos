# Navigation Demos for the Turtlebot 2

This repository provides ROS workspace configurations for running Turtlebot 2 demosin a Gazebo simulation environment.  It relies also on a [fake localization package](https://github.com/TurtlebotAdventures/gazebo_fake_localization.git) that provides robot 
odometry for the demos where the robot does not have a localization module.   The package provides a topic that publishes perfect localization from the Gazebo 
robot state.  Taken together, the repositories provide a good entry point for understanding how ROS combines distinct modules in support of robot functionality.
Initial demos involve more user input to guide the robot, while more advanced ones require less and involve more robot autonomy. Once they are fully understood, you 
should be in a good position to role out your own robot autonomy stack and to create customized code to suports task-level autonomy.  To run on the real robot would simply 
involve launching everything (but the Gazebo part) on an actual robot in its deployment environment.

### Contents

The various components of the demos are separate launch files that serve as examples using different combinations of modules to yield different behaviors. 
Component launch files (found in launch/includes):

- localize using amcl (amcl_localization.launch.xml)
- make a map (while localizing) using gmapping (gmapping.launch.xml)
- publishing a known map (map_server.launch.xml)
- navigate (move_base.launch.xml)
- localize perfectly using internal state of simulator (perfect_localization.launch.xml)

Current examples:

- navigating and making a map as you go (nav_mapping.launch)
- navigating and localizing using preexisting map (nav_localizing.launch)
- navigating with preexisting map and perfect localization (nav_known.launch)

The examples are deliberately simple and are to help you get familiar with creating and combining launch files.

Included is a Gazebo world that might look familiar to GT students (gazebo.launch) and a customized rviz configuration that shows most of the relevant topics (rviz.launch). 

_Note:_ For GT students, the lab workstations are already setup to have this repository installed and available.

### Understanding

Look through all of the launch files and try to understand what they are doing (with the exception of gazebo.launch; it is much more complicated and not particularly 
relevant for what you are doing). Return to the gazebo launch if you wish to understand how to create custom worlds and simulate them.  The ability to do so is essential 
since debugging in simulation is much safer and affords more effective access to intermediate information. Knowing this also aids in experience-based approaches to robot 
learning, like imitation learning and reinforcemnt learning.

The intent is for you to apply the lessons learned from these examples to create your own hierarchies of launch files. While you can <include> launch files from this
package in your own launch files, you will have much more flexibility if you create your own. Make your life easier by organizing your launch files so that you have to
launch as few as possible; keep in mind that everything in a launch file has to be started and stopped together* (*This isn't completely true, but to keep things 
simple, pretend that it is).

### Translation to Embodied Robotics

The examples are intended as self-contained demos for Gazebo and not for a real Turtlebot. What else is needed to run on the real robot? Try making your own launch 
files to run something like nav_mapping or nav_localizing on the real robot. (Hint: look at the content of the original demos launch files). What you learn doing 
this should help you with running your own projects in both real and simulated environments.

## Exploration Tip

The best way to advance and develop best coding practice is to create a git repo for the code associated to your personal explorations and modifications.
This includes launch files, parameters settings, etc. Git is an important version control system suited to asynchronous collaborative coding. Either the public
github or, for GT students, the enterprise GT github. You can put it in your personal account, for now at least. Just be sure to commit and push frequently (in 
collaborative settings, you would first create a branch and push to it so that other retain access to functional code). 
Using git ensures that you have a record of what you've changed and prevents you from losing everything due to computer issues. 
It is recommended that your repo is structured like a proper ROS package; this will make using your launch files much easier
([instructions here](http://wiki.ros.org/ROS/Tutorials/CreatingPackage)).  There are some exceptions to this rule, but early on these differencs are subtle to 
appreciate.
