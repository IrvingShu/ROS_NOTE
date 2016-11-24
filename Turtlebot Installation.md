# Turtlebot Installation

1. In addition, you will need to install the following debs for [TurtleBot](http://wiki.ros.org/TurtleBot) (please update this if you find any errors): 

```
> sudo apt-get install ros-indigo-turtlebot ros-indigo-turtlebot-apps ros-indigo-turtlebot-interactions ros-indigo-turtlebot-simulator ros-indigo-kobuki-ftdi ros-indigo-rocon-remocon ros-indigo-rocon-qt-library ros-indigo-ar-track-alvar-msgs
```

2. set env

   ```
   > export TURTLEBOT_BASE=create
   > export TURTLEBOT_STACKS=circles
   > export TURTLEBOT_3D_SENSOR=asus_xtion_pro    (alternatively kinect)
   > export TURTLEBOT_SERIAL_PORT=/dev/ttyUSB0    (may appear under another ttyUSBn)
   ```

3. Bringup

   ```
   roslaunch turtlebot_bringup minimal.launch --screen
   ```

4. move

   ```
   roslaunch turtlebot_teleop keyboard_teleop.launch --screen
   ```

