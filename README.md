Collaborative load lifting
==========================

By following the instructions below, it will be possible to download the code used in the Gazebo simulations discussed in the thesis "Modeling and control of a suspended load lifted by two aerial vehicles".

Note that this particular package contains the URDF model of the UAVs-load system analyzed in the thesis, and the launchfiles. The Phyton controller is in a separate repository.


### Installation

1. This package requires the multirotors models defined in the RotorS project. The RotorS package can be installed by following the instructions at 
~~~~
https://github.com/ethz-asl/rotors_simulator
~~~~
The instructions that follow assume that both ROS Indigo and RotorS have ben setup correctly.

2. Clone this repository in order to obtain the additional models,
~~~~
$ cd ~/catkin_ws/src
$ git clone https://github.com/massimilianop/collaborative_load_lifting.git
~~~~

3. Build the catkin workspace,
~~~~
$ cd ~/catkin_ws/
$ catkin_make
~~~~

4. There are two ways to obtain the controller. If you have acces to the Smart Mobility Lab private repository, the controller is included in the uav_control controller library. Otherwise, the controller can be also obtained from
~~~~
https://github.com/massimilianop/sml_under_development/tree/collaborative_load_lifting_branch
~~~~

Note that the controller is built in order to work within the control framework being used in the Smart Mobility Lab at KTH at the time of the writing of the thesis. The public version is provided as is, and may not be the most up to date one.


### Basic usage

Launch the simulator with the command
~~~~
roslaunch collaborative_load_lifting two_fireflies.launch
~~~~

Note that, by default, the simulation starts paused. If no path is being published, the UAVs lift the bar up to ground level.

A soecific path can be setup within the publisher, located at
~~~~
~/quad_control/scripts/collaborative_slung_load_lifting/bar_reference_publisher.py
~~~~

By editing the contents of bar_reference_publisher.py, it is possible to define a new path. Currently, a demo path is set up, and can be launched with the command
~~~~
rosrun quad_control bar_reference_publisher.py
~~~~

### Advanced usage

The target bar configuration can also be given from the terminal, by publishing a nav\_msgs/Path.msg type message in the topic /bar\_reference\_pose\_path.

Also note that the parameters the define load and cables can be given as arguements when launching the file two_fireflies.launch.


### Stability testing

This repository also contains the launchfiles test\_1.launch, test\_2.launch and test_3.launch, which where used to test the varius damping methods and controllers during the thesis work.

Additional detais on these launchfiles is discussed in the thesis. For the basic user, these files show an example on how to spawn the system in different configurations.
