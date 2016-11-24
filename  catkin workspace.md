Let's create a [catkin workspace](http://wiki.ros.org/catkin/workspaces): 

```
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
$ catkin_init_workspace
```

Even though the workspace is empty (there are no packages in the 'src' folder, just a single CMakeLists.txt link) you can still "build" the workspace: 

```
$ cd ~/catkin_ws/
$ catkin_make
```

The [catkin_make](http://wiki.ros.org/catkin/commands/catkin_make) command is a convenience tool for working with [catkin workspaces](http://wiki.ros.org/catkin/workspaces). If you look in your current directory you should now have a 'build' and 'devel' folder. Inside the 'devel' folder you can see that there are now several setup.*sh files. Sourcing any of these files will overlay this workspace on top of your environment. To understand more about this see the general catkin documentation: [catkin](http://wiki.ros.org/catkin). Before continuing source your new setup.*sh file: 

```
$ source devel/setup.bash
```

To make sure your workspace is properly overlayed by the setup script, make sure ROS_PACKAGE_PATH environment variable includes the directory you're in. 

```
$ echo $ROS_PACKAGE_PATH
/home/youruser/catkin_ws/src:/opt/ros/kinetic/share:/opt/ros/kinetic/stacks
```