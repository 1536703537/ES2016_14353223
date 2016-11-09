# report 
### student number：14353223
### name: 罗海福

* **Description**：

   	*	ROS（机器人操作系统，Robot Operating System），是专为机器人软件开发所设计出来的一套电脑操作系统架构。它是一个开源的元级操作系统（后操作系统），提供类似于操作系统的服务，包括硬件抽象描述、底层驱动程序管理、共用功能的执行、程序间消息传递、程序发行包管理，它也提供一些工具和库用于获取、建立、编写和执行多机融合的程序。
   	*	ROS的运行架构是一种使用ROS通信模块实现模块间P2P的松耦合的网络连接的处理架构，它执行若干种类型的通讯，包括基于服务的同步RPC（远程过程调用）通讯、基于Topic的异步数据流通讯，还有参数服务器上的数据存储。
*	**How to install**
	*	Configure your Ubuntu repositories
		*	Configure your Ubuntu repositories to allow "restricted," "universe," and "multiverse." You can follow the Ubuntu guide for instructions on doing this
	*	Setup your sources.list
		*	Setup your computer to accept software from packages.ros.org. ROS Jade ONLY supports Trusty (14.04), Utopic (14.10) and Vivid (15.04) for debian packages.
		
		`sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`
	*	Set up your keys
		`sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116`
	*	Installation
		*	First, make sure your Debian package index is up-to-date: 
			`sudo apt-get update`
		*	There are many different libraries and tools in ROS. We provided four default configurations to get you started. You can also install ROS packages individually. 
			*	Desktop-Full Install: (Recommended) : ROS, rqt, rviz, robot-generic libraries, 2D/3D simulators, navigation and 2D/3D perception 
			`sudo apt-get install ros-jade-desktop-full`
		*	To find available packages, use: 
			`apt-cache search ros-jade`
	*	Initialize rosdep
		*	Before you can use ROS, you will need to initialize rosdep. rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS. 
		*		
			`sudo rosdep init`
			`rosdep update`
		![](http://tuku02-qn.icp114.cn/public/16-11-9/63253661.jpg)
	*	Environment setup
		*	It's convenient if the ROS environment variables are automatically added to your bash session every time a new shell is launched: 
			`echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc`
			`source ~/.bashrc`
		*	If you just want to change the environment of your current shell, you can type: 
			`source /opt/ros/jade/setup.bash`
		![](http://tuku02-qn.icp114.cn/public/16-11-9/25719124.jpg)
	*	Getting rosinstall
		*	rosinstall is a frequently used command-line tool in ROS that is distributed separately. It enables you to easily download many source trees for ROS packages with one command.

		*	To install this tool on Ubuntu, run: 
			`sudo apt-get install python-rosinstall`	
		
*	**Experimental experience**
		![](http://tuku02-qn.icp114.cn/public/16-11-9/91187783.jpg)
	*	If you know the location of the repository of each package, you know you can obtain all the code there. But it's often hard even for experienced developers to reach the correct maintained repository of certain packages. Also, in some situations you just want to get the source of the released, installed version of a package. The methods described here the best for these cases. 
	*	本次实验是要我们安装配置ROS，是因为ROS上有许多SLAM算法及对应的数据集可以用，ROS是robot operation system 是一套框架，底层提供硬件驱动，软件层面支持通用的文件格式，我们主要是用他的仿真功能，这次配置ROS的实验总体上没有那么多困难，按照[ROS安装配置教程](http://wiki.ros.org/jade/Installation/Ubuntu)一步步走就好了，就完成了ROS的配置，但是还不知道该如何使用。