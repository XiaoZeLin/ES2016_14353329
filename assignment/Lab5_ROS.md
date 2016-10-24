# Lab5： Ubuntu 安装  ROS



_ _ _



##### 概要



随着机器人领域的快速发展和复杂化，代码的复用性和模块化的需求原来越强烈，而已有的开源机器人系统又不能很好的适应需求。2010年Willow Garage公司发布了开源机器人操作系统ROS（robot operating system），很快在机器人研究领域展开了学习和使用ROS的热潮。



 ROS是开源的，是用于机器人的一种后操作系统，或者说次级操作系统。它提供类似操作系统所提供的功能，包含硬件抽象描述、底层驱动程序管理、共用功能的执行、程序间的消息传递、程序发行包管理，它也提供一些工具程序和库用于获取、建立、编写和运行多机整合的程序。



##### 安装ROS-jade

ROS的安装当然是我们开始动手的第一步了，这里我们使用的操作系统是ubuntu，因为ROS在ubuntu上的支持是最好的。不过，首先提醒本文安装方法只适用于Ubuntu14.04、14.10和15.04。而且ROS的版本是紧跟着Ubuntu的版本更新的！



1. 配置Ubuntn的软件源

   配置Ubuntu要求允许接受restricted、universe和multiverse的软件源,可以根据下面的链接配置:

    ![](http://upload-images.jianshu.io/upload_images/273380-3f5b0289d8e8e560.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 添加软件源到sources.list
   ```
   sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
3. 设置密钥
      ```
   sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116
```
4. 命令行安装ROS（最好安装桌面完整版desktop-full）
   ```
  sudo apt-get update
  sudo apt-get install ros-jade-desktop-full
```

5. 初始化rosdep
```
   sudo rosdep init
   rosdep update
```
6. 设置环境（添加ROS的环境变量,这样,当你打开你新的shell时,你的bash回话中会自动添加环境变量.）

 ```
   echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc
   source ~/.bashrc
```
6. 安装rosinstall（rosinstall命令是一个使用的非常频繁的命令,使用这个命令可以轻松的下载许多ROS软件包。）
```
sudo apt-get install python-rosinstall
```



##### 实验感想

 ROS中提供了很多强大的功能，我们学习完上面的基本知识之后要继续进行深入。既然安装了如此厉害的机器人操作系统ROS，我肯定要用它来弄有趣的东西：我们可以在里面创建自己的机器人，并且让机器人动起来。还可以创建地图，显示3D点云等等，总之，想在ROS中显示的东东都可以在这里显示出来。当然这些显示都是通过消息的订阅来完成的，机器人通过ROS发布数据，rviz订阅消息接收数据，然后显示，这些数据也是有一定的数据格式的。

 

 

 

 ![](http://img.blog.csdn.net/20130430210942974)





_ _ _



