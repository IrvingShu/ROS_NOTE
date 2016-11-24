### 先决条件

在本教程中我们将使用到一个轻量级的模拟器，请使用以下命令来安装： 

```
$ sudo apt-get install ros-<distro>-ros-tutorials
```

用你使用的ROS发行版本名称(例如electric、fuerte、groovy、hydro等)替换掉'<distro>'。 

### 图概念概述

- [Nodes](http://wiki.ros.org/Nodes):节点,一个节点即为一个可执行文件，它可以通过ROS与其它节点进行通信。 
- [Messages](http://wiki.ros.org/Messages):消息，消息是一种ROS数据类型，用于订阅或发布到一个话题。 
- [Topics](http://wiki.ros.org/Topics):话题,节点可以发布消息到话题，也可以订阅话题以接收消息。 
- [Master](http://wiki.ros.org/Master):节点管理器，ROS名称服务 (比如帮助节点找到彼此)。 
- [rosout](http://wiki.ros.org/rosout): ROS中相当于stdout/stderr。 
- [roscore](http://wiki.ros.org/roscore): 主机+ rosout + 参数服务器 (参数服务器会在后面介绍)。 

### 节点

一个节点其实只不过是ROS程序包中的一个可执行文件。ROS节点可以使用ROS客户库与其他节点 

通信。节点可以发布或接收一个话题。节点也可以提供或使用某种服务。 

### 客户端库

ROS客户端库允许使用不同编程语言编写的节点之间互相通信: 

- rospy = python 客户端库 
- roscpp = c++ 客户端库  

### roscore

roscore 是你在运行所有ROS程序前首先要运行的命令。   

请运行: 

```
$ roscore
```

然后你会看到类似下面的输出信息: 

```
... logging to ~/.ros/log/9cf88ce4-b14d-11df-8a75-00251148e8cf/roslaunch-

machine_name-13039.log
Checking log directory for disk usage. This may take awhile.
Press Ctrl-C to interrupt
Done checking log file disk usage. Usage is <1GB.

started roslaunch server http://machine_name:33919/
ros_comm version 1.4.7

SUMMARY
========

PARAMETERS
 * /rosversion
 * /rosdistro

NODES

auto-starting new master
process[master]: started with pid [13054]
ROS_MASTER_URI=http://machine_name:11311/

setting /run_id to 9cf88ce4-b14d-11df-8a75-00251148e8cf
process[rosout-1]: started with pid [13067]
started core service [/rosout]
```

如果 roscore 运行后无法正常初始化，很有可能是存在网络配置问题。参见

[网络设置——单机设置](http://www.ros.org/wiki/ROS/NetworkSetup#Single_machine_configuration) 

如果 roscore 不能初始化并提示缺少权限，这可能是因为~/.ros文件夹 

归属于root用户（只有root用户才能访问），修改该文件夹的用户归属关系： 

```
$ sudo chown -R <your_username> ~/.ros
```

### 使用rosnode

打开一个**新的终端**, 可以使用 **rosnode** 像运行 roscore 一样看看在 

运行什么... 

**注意:** 当打开一个新的终端时，你的运行环境会复位，同时你的~/.bashrc  

文件会复原。如果你在运行类似于rosnode的指令时出现一些问题，也许你需要添加 

一些环境设置文件到你的~/.bashrc或者手动重新配置他们。 

rosnode  显示当前运行的ROS节点信息。rosnode list 指令列出活跃的节点: 

```
$ rosnode list
```

- 你会看到: 

  ```
  /rosout
  ```

这表示当前只有一个节点在运行: [rosout](http://wiki.ros.org/rosout)。因为这个节点用于收集和记录节点调 

试输出信息，所以它总是在运行的。 

rosnode info 命令返回的是关于一个特定节点的信息。 

```
$ rosnode info /rosout
```

这给了我们更多的一些有关于rosout的信息, 例如，事实上由它发布 

/rosout_agg. 

```
------------------------------------------------------------------------
Node [/rosout]
Publications:
 * /rosout_agg [rosgraph_msgs/Log]

Subscriptions:
 * /rosout [unknown type]

Services:
 * /rosout/set_logger_level
 * /rosout/get_loggers

contacting node http://machine_name:54614/ ...
Pid: 5092
```

现在，让我们看看更多的节点。为此，我们将使用rosrun 弹出另一个节点。 

### 使用 rosrun

rosrun  允许你使用包名直接运行一个包内的节点(而不需要知道这个包的路径)。 

用法: 

```
$ rosrun [package_name] [node_name]
```

现在我们可以运行turtlesim包中的 turtlesim_node。  

然后, 在一个 **新的终端**: 

```
$ rosrun turtlesim turtlesim_node
```

你会看到 turtlesim 窗口: 

- ![turtlesim.png](http://wiki.ros.org/cn/ROS/Tutorials/UnderstandingNodes?action=AttachFile&do=get&target=turtlesim.png)

