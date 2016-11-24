### 1. 编译程序包

一旦安装了所需的系统依赖项，我们就可以开始编译刚才创建的程序包了。 

**注意:** 如果你是通过apt或者其它软件包管理工具来安装ROS的，那么系统已经默认安装好所有依赖项。 

记得事先source你的环境配置(setup)文件，在Ubuntu中的操作指令如下： 

```
$ source /opt/ros/groovy/setup.bash
```

#### 使用 catkin_make

[catkin_make](http://wiki.ros.org/catkin/commands/catkin_make) 是一个命令行工具，它简化了catkin的标准工作流程。你可以认为[catkin_make](http://wiki.ros.org/catkin/commands/catkin_make)是在CMake标准工作流程中依次调用了cmake 和 make。 

使用方法: 

```
# 在catkin工作空间下
$ catkin_make [make_targets] [-DCMAKE_VARIABLES=...]
```

CMake标准工作流程主要可以分为以下几个步骤： 

**注意:** 如果你运行以下命令是无效的，因为它只是一个演示CMake工作流程的例子。 

```
# 在一个CMake项目里
$ mkdir build
$ cd build
$ cmake ..
$ make
$ make install  # (可选)
```

每个CMake工程在编译时都会执行这个操作过程。相反，多个catkin项目可以放在工作空间中一起编译，工作流程如下： 

```
# In a catkin workspace
$ catkin_make
$ catkin_make install  # (可选)
```

上述命令会编译src文件夹下的所有catkin工程。想更深入了解请参考[REP128](http://ros.org/reps/rep-0128.html)。 如果你的源代码不在默认工作空间中（~/catkin_ws/src),比如说存放在了my_src中，那么你可以这样来使用catkin_make: 