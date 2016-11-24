1. create package

catkin_create_pkg turtlebot_move std_msgs rospy roscpp

2. edit cpp

3. modify CMakeList.txt

   add_executable(send_goal src/send_goal.cpp)

   target_link_libraries(send_goal ${catkin_LIBRARIES})

4. cd ~/catkin_ws

5. catkin_make

   ​