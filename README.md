# dual_ur

本repo包括专门为实验室的双臂UR5设计的一系列ROS package。



## 依赖

* ROS Noetic
* MoveIt!



## 安装
安装依赖的package（可根据需要选择性安装）:
```
cd <YOUR_PATH>/catkin_ws/src

# ur 的 description 和 moveit config
git clone https://github.com/THU-DA-Robotics/universal_robot.git -b calibration_devel

# 用于驱动真实 ur
git clone https://github.com/THU-DA-Robotics/Universal_Robots_ROS_Driver.git

# robotiq 夹爪
git clone https://github.com/THU-DA-Robotics/robotiq.git -b noetic_devel
```

Clone the repo:

```
cd <YOUR_PATH>/catkin_ws/src
git clone https://github.com/THU-DA-Robotics/dual_ur.git
```

安装 dependencies：

```
$ sudo apt update -qq
$ rosdep update
$ rosdep install --from-paths src --ignore-src -y
```




## 使用

目前已写好的模型：
* dual_ur5
* dual_ur5_robotiq2f85

以下命令说明以 dual_ur5 为例。

记得要先：
```
source devel/setup.bash
```

### dual_ur_description




#### rviz中可视化 xacro
```
roslaunch dual_ur_description view_dual_ur5.launch
```

#### xacro 转为 urdf
```
cd src/dual_ur/dual_ur_description/urdf
rosrun xacro xacro -o dual_ur5.urdf dual_ur5.urdf.xacro
```


### xxx_moveit_config

#### 创建/修改

```
roslaunch moveit_setup_assistant setup_assistant.launch
```
若要基于 xacro 文件创建新的 moveit_config 包，则点击 Create New Moveit Configuration Package，再选中相应的 xacro 文件。

若要修改，则点击 Edit Existing Moveit Configuration Package，再选中 dual_ur5_moveit_config 文件夹，再点击右下角的 Load Files。

具体配置方法参考 [MoveIt Setup Assistant](https://ros-planning.github.io/moveit_tutorials/doc/setup_assistant/setup_assistant_tutorial.html#moveit-setup-assistant)。

**TIPs**: 
* 在生成了 xxx_moveit_config 包后，想再修改原始的 xacro 文件名称就很困难了，可能需要完全重新使用 MoveIt Setup Assistant 配置一遍，或者手动对所有文件中的索引名称进行修改。

#### rviz中简单使用moveit

```
roslaunch dual_ur5_moveit_config demo.launch
```





### dual_ur_ros_driven (待开发)

用于真实机器人的使用。


启动bring up，同时启动rviz显示双臂机器人状态。
```
roslaunch dual_ur_ros_driver dual_ur5_bringup.launch
```





## TODO
* 右臂的 External Control 未配置。
* dual_ur_ros_driven 未更新，待开发。







