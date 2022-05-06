## 双臂支架的URDF

从solidworks导出。
复制整理进 /dual_ur_description，注意其中有些文件内的路径要修改。



## Moveit Setup Assistant

* 注意设置planning_group的时候，base_link_base_joint不能添加进去，否则的话，整个group就不是一个chain了。
* Kinematic Solver 不能选择 ur_kinematics，存在关节名称命名不一致。因为现在关节名称前加了arm_x_了。
* 不能同时打开两个 moveit setup assistant。
* 机器人初始关节角可以在 fake_controller.yaml 里进行设置。

## MoveIt








## 参考资料

* [Can't simultaneously control multiple robots](https://github.com/UniversalRobots/Universal_Robots_ROS_Driver/issues/81#issuecomment-578418515)
* [MACS Dual-Arm Robots ROS Driver](https://github.com/macs-lab/macs_dual_arm)

