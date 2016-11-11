# Ubuntu下安装ROS

## ROS简介
ROS，即robot operating system，机器人操作系统，提供一系列程序库和工具帮助软件开发者创建机器人，应用软件，提供了硬件抽象、设备驱动、库函数、可视化、消息传递和软件包管理等诸多功能。
## 安装教程
### 配置Ubuntu软件仓库
Ubuntu的软件仓库有main、restricted、universe和multiverse共4种安装模式，这里我们要设置允许后面3种。
### 添加sources.list
配置电脑使其能够安装来自packages.ros.org的软件包。<br>
（sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'）
### 添加keys
（sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116）
### 安装
首先确认Debian的软件包索引是最新的。<br>
（sudo apt-get update）<br>
然后安装桌面完整版的ROS，其中包含ROS、rqt、rviz、通用机器人函数库、2D/3D仿真器、导航以及2D/3D感知功能。
### 初始化rosdep
（sudo rosdep init）<br>
（rosdep update）
### 环境配置
使得每次开启一个新的终端ROS环境变量都能够自动配好<br>
（echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc）<br>
（source ~/.bashrc）
### 安装rosinstall
（sudo apt-get install python-rosinstall）
