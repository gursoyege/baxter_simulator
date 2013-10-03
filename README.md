baxter_simulator
=============
RSDK Wiki: http://github.com/RethinkRobotics/sdk-docs/wiki

## Repository Description
Necessary files for the Gazebo™ simulation of the Baxter Research Robot from Rethink Robotics Inc.


## Prequisites

 * [ROS Groovy](http://wiki.ros.org/groovy/Installation)
 * Setup Github - the git@github.com urls, below, only work if you have [Setup Github](https://help.github.com/articles/set-up-git) and generated [SSH Keys for Github](https://help.github.com/articles/generating-ssh-keys).
 * Install gazebo_ros_pkgs from source as detailed on [this tutorial](http://gazebosim.org/wiki/Tutorials/1.9/Installing_gazebo_ros_Packages)


## Baxter Installation

* Create a catkin workspace and cd into it:

```
    mkdir -p ~/catkin_ws/src
    cd ~/catkin_ws/src
    catkin_init_workspace
```

* install from source a few customized repositories:

Install gazebo ros pkgs

git clone https://github.com/RethinkRobotics/gazebo_ros_pkgs.git -b hydro-devel

```
    git clone git@github.com:RethinkRobotics/baxter_simulation.git -b development
    git clone git@github.com:RethinkRobotics/sdk-examples.git -b gazebo_dev
    git clone git@github.com:RethinkRobotics/baxter_common.git -b development
    git clone http://github.com/RethinkRobotics/ros_controllers -b velocity_position_controller
    git clone https://github.com/RethinkRobotics/ros_control.git
    git clone https://github.com/RethinkRobotics/control_toolbox.git
    git clone https://github.com/RethinkRobotics/realtime_tools.git

```

* Install dependencies

```
    cd ~/catkin_ws/
    rosdep install --from-paths . --ignore-src --rosdistro groovy -y
```

* Build

```
    catkin_make
```
You may need to run this command multiple times if there is a message dependency issue.

### Simulation 

 * Start simulation with controllers:
   ```
   roslaunch baxter_gazebo baxter_world.launch
   ```
   By default the position controllers are started. To switch, use the JointCommandMode topic as documented in the Baxter SDK.

 * Optional: Test/tune the velocity controllers or position controllers using a RQT dashboard GUI. Make sure you are in the right joint command mode when using these:

   ```
   roslaunch baxter_control baxter_sdk_position_rqt.launch
   ```
   or
   ```
   roslaunch baxter_control baxter_sdk_velocity_rqt.launch 
   ```

## Start MoveIt

Works with simulation or hardware:

 * Start MoveIt:

   ```
   roslaunch baxter_moveit_config baxter_bringup.launch
   ```

## Develop and Contribute

See [Contribute](https://github.com/osrf/baxter/blob/master/CONTRIBUTING.md) page.
