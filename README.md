romeo_dcm_robot
===============

DCM stack integrating tools to control Romeo robot

Installation
------------

- install dependencies

        sudo apt-get install ros-indigo-romeo-robot ros-indigo-romeo-control ros-indigo-naoqi-dcm-driver

- then, install [romeo_dcm_bringup](http://wiki.ros.org/romeo_dcm_bringup) or compile it from source

        sudo apt-get install ros-indigo-romeo-dcm-bringup

- optionally, install [romeo_moveit_config](http://wiki.ros.org/romeo_moveit_config)

        sudo apt-get install ros-indigo-romeo-moveit-config

How to use it 
--------------

To command your robot remotely with ros control :

- start the DCM Bringup providing the robot's IP

        roslaunch romeo_dcm_bringup romeo_dcm_bringup_remote.launch robot_ip:=<ROBOT_IP>

- Wait until romeo_dcm_bringup node is ready, then start MoveIt! and control the robot:

        roslaunch romeo_moveit_config moveit_planner.launch

- or you can send a trajectory to the desired controller (actionlib)

        rosrun actionlib axclient.py <name of the goal topic of the action server>

example:

        rosrun actionlib axclient.py /romeo_dcm/LeftArm_controller/follow_joint_trajectory/goal

To choose the controllers you want to load at launchtime you have to modify romeo_control/launch/romeo_control_traject$
To know the list of controllers implemented please refer to : romeo_control/config/romeo_trajectory_control.yaml
You can start and stop the ros-controllers using the rqt plugin ControllerManager
