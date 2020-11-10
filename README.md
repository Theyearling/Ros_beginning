# Ros_begening
# some problem in ros-learning

# rosdep init、upgate:
主要原因是网速和墙<br>
 1.建议换成手机热点<br>
 2.爪巴墙，<br>https://github.com/Qv2ray/Qv2ray<br>
           https://github.com/v2fly/v2ray-core/releases<br>
    搭建梯子出墙，一切就迎刃而解。

# gazebo参数出错：
 export SVGA VGPU10=0

# Contronller does not exit：
 sudo apt-get install ros*contronller*
 
# 添加依赖不成功：
 [ROS packages for Kinetic]( http://repositories.ros.org/status_page/ros_noetic_default.html)<br>
 [ROS packages for Noetic](http://repositories.ros.org/status_page/ros_noetic_default.html)<br>
 可以看到noetic至少少了1000+的依赖包，只能自行下载package到/home/theyearling/catkin_ws/src
 
 # catkin_make出错：
    hector_mappingConfig.cmake
    hector_mapping-config.cmake
  **solve:**
    
   **1.下载package到catkin_ws/src**
    
    git clone https://github.com/ros-perception/slam_gmapping.git
    git clone https://github.com/tu-darmstadt-ros-pkg/hector_slam.git
    
   **2.修改相应的package.xml**
    
    <build_depend>gmapping</build_depend>
    <build_depend>hector_mapping</build_depend>

    <run_depend>gmapping</run_depend>
    <run_depend>hector_mapping</run_depend>
    
 # 安装依赖：
    rosdep install --from-paths src --ignore-src --rosdistro=noetic -y
