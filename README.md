
# Ustbot Mobile Platform (SLAM, SIM, NAV)

This repo is meant to be used as a testing environment for hyperparameters fine tunning (*navigation planners* and *costmaps*). The file structure is similar to the existing one inside the robot or at least to the codebase I was shared. Inside 'src' the most relevant forlders to look are Navigation and Simulation.

\
This repo contains turtlebot packages as a reference, guidance and debugging, that's the reason you will see some files ending with 'ustbot' or 'burger' or packages starting with 'turtlebot' (as an example). In the future these packages are meant to be removed and a new/proper naming for the files will be used instead. 

## Main forlders
    Bringups
      Inside this folder you will find your typical bringup packages.
    Navigation
      Inside this folder everything related to nav is here.
      4 packages: lidar sensor fusion, slam, teleop, and nav.
    Simulation
      Inside this folder everything related sim is here.
      2 packages, robot descriptions and sim.
      Worlds and Modesls.

## Installed Dependencies
    sudo apt-get install ros-<version>-rosserial 

    sudo apt-get install python3-empy 

    sudo apt-get install ros-<version>-map-server 

    sudo apt-get install ros-<version>-move-base 

    sudo apt-get install ros-<version>-navigation 

    sudo apt-get install ros-<version>-slam-gmapping 

    sudo apt-get install ros-<version>-ros-control 

    sudo apt-get install ros-<version>-ros-controllers 

    sudo apt-get install ros-<version>-global-planner 

    sudo apt-get install ros-<version>-dwa-local-planner 

    sudo apt-get install ros-<version>-eband-local-planner 

    sudo apt-get install ros-<version>-teb-local-planner 

    sudo apt-get install ros-<version>-mpc-local-planner 


## Environment Variables

To run this project, you will need to add the following environment variables.


`WORLDS_PATH`=~/YOUR_ROS_WORKSPACE/src/Simulation/Worlds 

`MOBILEBOT_MODEL`=ustbot 

`TURTLEBOT3_MODEL`=burger 

`SIMULATION_MODELS_PATH`=~/YOUR_ROS_WORKSPACE/src/Simulation/Models 

These two variables dont do anymore what they did at the beginning but we have to define them nonetheless because I havent change the logic inside the launch files (xdxd). WHenever you want to test a planner **YOU HAVE TO CHANGE these variables** accordingly AND change the **move_base_params.yaml**

\
`LOCAL_PLANNER`=teb (e.g. teb, dwa, base, mpcqf) 

`GLOBAL_PLANNER`=global  (navfn, teb)
## Usage/Example SLAM

The following launch file will open the chosen simulation, in this example maze_world.

```bash
roslaunch mobilebot_gazebo mobilebot_maze_world.launch
```

To start SLAM run the following launch file (choose your favorite method: gmapping, cartographer, hector, karto, frontier_exploration):
```bash
roslaunch mobilebot_slam mobilebot_slam.launch slam_methods:=gmapping
```
In mobilebot_slam package, inside *config* folder you have access to params used by the slam methods.


## Usage/Example NAV

The following launch file will open the chosen simulation, in this example maze_world.

```bash
roslaunch mobilebot_gazebo mobilebot_maze_world.launch
```

To start navigation run the following launch file.

```bash
roslaunch mobilebot_navigation mobilebot_navigation.launch
```
In mobilebot_navigation package, inside *config* folder you have access to all the params used by move_base, costmaps and planners (global and local). 

## Usage/Example TELEOP
The folowwing launch file will give you teleoperation control under the robot model through the terminal.

```bash
roslaunch mobilebot_teleop mobilebot_teleop_key.launch
```

## Usage/Example Bringup
The folowwing launch file will call the ustbot bringup state.

```bash
roslaunch ustbot_bringup ustbot_model.launch
```
