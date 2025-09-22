## UP70 9月培训总结
**$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad$文潇墨 2025-09-21**

<img width="1725" height="1920" alt="Untitled diagram _ Mermaid Chart-2025-09-22-041935" src="https://github.com/user-attachments/assets/8d6c4520-d365-4d8a-bbaa-b095b45c048c" />


整个大作业可以大致分为**软件和硬件层两个板块**。目前跑通了软件层，由于时间原因暂未实机部署到实体机器人上测试。软件层这里分成了三个板块：**SLAM算法、驱动及功能包、导航算法**。以下是细化描述：

### 1.驱动及功能包

源码地址：https://github.com/vishomework/ros2_driver/tree/dev_wxm ， 所有需要注意的细节和踩的坑都可见该仓库 README.md（Ubuntu输入法坏了，故仓库readme用英文写的）。
该仓库现有两个大板块：`ros2_driver` 和 `functional_packages`, 下面分别对二者做简要介绍：

#### （I）ros2_driver
`ros2_driver` 是一个集成多传感器驱动的驱动包，目前能一键驱动RoboSense系列雷达和ms200线雷达。实机已正常配置雷达IP并使其正常发出话题 `/livox_lidar` 和 `/MS200/scan`（效果见下图）， 并且能正常发出 `/tf` 话题。
<img width="917" height="728" alt="be8453d86dda64583f0c35607706d24d" src="https://github.com/user-attachments/assets/f33f144b-af49-4294-a8fe-7fa79c073466" />
<img width="481" height="349" alt="e3ac2618df128f2501ec883f07c544db" src="https://github.com/user-attachments/assets/3659b431-8631-40e6-8ffb-4469811d63f4" />
<img width="394" height="205" alt="bae33133d8baca4fdbd417c0ae97a679" src="https://github.com/user-attachments/assets/d5d68897-8775-4dbb-afff-070c805a90cd" />




#### （II）functional_packages
`functional_packages` 里有两个桥接包， 分别是 `ROS2-ROS1 Bridge` 和 `foxglove_bridge`，前者实现了ROS2和ROS1系统的桥接，实测ROS1容器能与主机ROS2系统正常通信Topics(见上部分图）。后者把话题转发到foxglove端口显示，如图，实测foxglove和rviz都可以正常实现可视化（测试使用的是HKU-Mars实验室的数据包）。
<img width="1269" height="664" alt="793d292732f28a1033e47c7cbe77ecec" src="https://github.com/user-attachments/assets/2548af89-e047-44e8-bf39-a755ed4f1a5d" />

### 2.SLAM算法部分

源码地址：https://github.com/vishomework/VoxelSlam/tree/dev_wxm ， 所有需要注意的细节和踩的坑都可见该仓库 README.md（Ubuntu输入法坏了，故仓库readme用英文写的）。

