# Use the Baxter robot to grab the coke can from the side

## 1.First time Set up
First you need to download the ROS_noetice version,you can download from here http://wiki.ros.org/kinetic/Installation/Ubuntu

Then,Create a ROS environment and download the necessary packages,You can use the following commands:
```
mkdir -p $HOME/Coke_ws/src
git clone https://github.com/rojas70/hlearning_ros_external_pkgs_noetic.git
git clone https://github.com/rojas70/learning_ros_noetic.git
git clone https://github.com/fcr032899/MAGE5755-final-project
 ```
## 2.Build the workspace
```
cd cd $HOME/Coke_ws/
Catkin_make
````
## 3.Run cmd to grab coke can from side
Before running cmd,please 
```
souce ./devel/setup.bash
```
1st cmd:  Start an empty gazebo world
```
roslaunch  gazebo_ros  empty_world.launch
```
2nd cmd:  Add baxter robots, tables, coke cans and other objects
```
roslaunch baxter_variations baxter_on_pedestal_w_kinect_coke.launch 
```
3rd cmd:  Start RVIZ and make the baxter robot arm in pre_pose
```
roslaunch coordinator coord_vision_manip_coke.launch
```
4th cmd : Grab coke can
```
rosrun coordinator acquire_coke_can_client
```
5th cmd :Put down the coke can
```
rosrun coordinator dropoff_coke_can_client
```
You can watch the full simulation process form :

# Notice 
When using the baxter robot to grab the coke can, you may encounter the situation where the baxter grabbing width is not enough. You need to change the finger extension from narrow to wide in the right_end_effector.urdf.xacro in the baxter robot.









