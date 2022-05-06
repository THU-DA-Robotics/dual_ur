# dual_ur

本repo包括专门为实验室的双臂UR5设计的一系列ROS package。

## 依赖

* ROS Noetic
* MoveIt!



## 安装
安装 Universal_Robots_ROS_Driver 和 universal_robot:
```
cd <YOUR_PATH>/catkin_ws

# clone the driver
$ git clone https://github.com/THU-DA-Robotics/Universal_Robots_ROS_Driver.git src/Universal_Robots_ROS_Driver

# clone fork of the description. This is currently necessary, until the changes are merged upstream.
$ git clone -b calibration_devel https://github.com/THU-DA-Robotics/universal_robot.git src/universal_robot

# install dependencies
$ sudo apt update -qq
$ rosdep update
$ rosdep install --from-paths src --ignore-src -y
```

下载本pkg。




## 使用
记得要先：
```
source devel/setup.bash
```


### dual_ur_description

#### dual_ur.urdf.xacro 转为 dual_ur.urdf

```
cd src/dual_ur/dual_ur_description/urdf
rosrun xacro xacro -o dual_ur.urdf dual_ur.urdf.xacro
```
#### rviz中可视化urdf

```
# 需要先获得dual_ur.urdf文件
roslaunch dual_ur_description visualize_urdf.launch
```



### dual_ur_moveit_config

#### 对moveit_config进行修改

```
roslaunch moveit_setup_assistant setup_assistant.launch
```

点击 Edit Existing Moveit Configuration Package，再选中 dual_ur_moveit_config 文件夹，再点击右下角的 Load Files。

具体配置方法参考 [MoveIt Setup Assistant](https://ros-planning.github.io/moveit_tutorials/doc/setup_assistant/setup_assistant_tutorial.html#moveit-setup-assistant)。

#### rviz中简单使用moveit

```
roslaunch dual_ur_moveit_config demo.launch
```





### dual_ur_ros_driven

用于真实机器人的使用。


启动bring up，同时启动rviz显示双臂机器人状态。
```
roslaunch dual_ur_ros_driver dual_ur5_bringup.launch
```





## TODO
* 右臂的 External Control 未配置。







