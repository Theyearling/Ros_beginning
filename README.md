# Ros_begeinning
# some problem in ros-learning

# 安装ROS时设置key
 sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116<br>
 如果无法连接上述服务器，可以尝试hkp://pgp.mit.edu:80或者hkp://keyserver.ubuntu.coｍ<br>

# sudo apt-get update出现:由于没有公钥，无法验证下列签名：NO_PUBKEY F42ED6FBAB17C654
  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F42ED6FBAB17C654　对应输出的数字

# rosdep init、upgate:
主要原因是网速和墙<br>
 1.建议换成手机热点<br>
 2.爪巴墙，<br>https://github.com/Qv2ray/Qv2ray<br>
           https://github.com/v2fly/v2ray-core/releases<br>
    搭建梯子出墙，一切就迎刃而解。<br>
    **sudo chmod a+x Qv2ray.v2.6.3.linux-x64.AppImage**<br>
# gazebo参数出错：
 export SVGA VGPU10=0
 
# gazebo360°旋转：
 shift+旋转、鼠标左右中建各有功能

# Contronller does not exit：
 sudo apt-get install ros*contronller*
 
# 添加依赖不成功：
 [ROS packages for Kinetic]( http://repositories.ros.org/status_page/ros_kinetic_default.html)<br>
 [ROS packages for Noetic](http://repositories.ros.org/status_page/ros_noetic_default.html)<br>
 可以看到noetic少了1000+的依赖包，只能自行下载package到/home/theyearling/catkin_ws/src
 
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

# flashfxp与Ubuntu16.04文件传递：
  sudo  apt-get  install  vsftpd //Ubuntu下载vsftpd
  
  sudo  gedit  /etc/vsftpd.conf //修改配置文件<br>
  #local_enable=YES<br>
  #write_enable=YES //去掉#号
  
  sudo  /etc/init.d/vsftpd  start //启动命令<br>
  sudo  /etc/init.d/vsftpd  stop //关闭命令
  
# 没有安装相应的ros控制软件包 
    Could not load controller 'joint_state_controller' because controller type 'joint_state_controller/JointStateController' does not exist.
    Could not load controller 'joint_position_controller' because controller type 'joint_position_controller/JointPositionController' does not exist.
    Could not load controller 'joint_velocity_controller' because controller type 'joint_velocity_controller/JointVelocityController' does not exist.
    
  __solve:__<br>
      sudo apt-get install ros-kinetic-joint-state-controller<br>
      sudo apt-get install ros-kinetic-position-controllers<br>
      sudo apt-get install ros-kinetic-velocity-controllers<br>
    
  **advice:**<br>
    sudo apt-get install ros-kinetic-effort-controllers <br>
    sudo apt-get install ros-kinetic-joint-trajectory-controller
        
# GazeboRosControlPlugin missing \<legacyModeNS> ： 
  urdf 描述文件中，对 gazebo 插件描述添加 <legacyModeNS>true</legacyModeNS><br>
  
![image](https://github.com/Lillal/Ros_begening/blob/main/IMG/legacyModeNS.png)

# 运行Turtlebot时出现'TURTLEBOT_GAZEBO_WORLD_FILE' is not set
  export TURTLEBOT_GAZEBO_WORLD_FILE=/opt/ros/kinetic/share/turtlebot_gazebo/worlds/playground.world

# 调节鼠标灵敏度
    xinput --list //查看设备id
    xinput --list-props id //查看对应id设备的相关参数
    xinput --set-prop id 设备对应的参数标识 0.3 0 0 0 0.3 0 0 0 1 //默认参数为:1 0 0 0 1 0 0 0 1
  
# /etc/apt/sources.list
    # deb cdrom:[Ubuntu 16.04.7 LTS _Xenial Xerus_ - Release amd64 (20200806)]/ xenial main restricted

    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    # newer versions of the distribution.
    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial main restricted
    # deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial main restricted

    ## Major bug fix updates produced after the final release of the
    ## distribution.
    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial-updates main restricted
    # deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    ## team. Also, please note that software in universe WILL NOT receive any
    ## review or updates from the Ubuntu security team.
    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial universe
    # deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial universe
    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial-updates universe
    # deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial-updates universe

    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    ## team, and may not be under a free licence. Please satisfy yourself as to 
    ## your rights to use the software. Also, please note that software in 
    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    ## security team.
    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial multiverse
    # deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial multiverse
    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial-updates multiverse
    # deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

    ## N.B. software from this repository may not have been tested as
    ## extensively as that contained in the main release, although it includes
    ## newer versions of some applications which may provide useful features.
    ## Also, please note that software in backports WILL NOT receive any review
    ## or updates from the Ubuntu security team.
    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
    # deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

    ## Uncomment the following two lines to add software from Canonical's
    ## 'partner' repository.
    ## This software is not part of Ubuntu, but is offered by Canonical and the
    ## respective vendors as a service to Ubuntu users.
    # deb http://archive.canonical.com/ubuntu xenial partner
    # deb-src http://archive.canonical.com/ubuntu xenial partner

    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial-security main restricted
    # deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial-security universe
    # deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    deb http://mirrors.ustc.edu.cn/ubuntu/ xenial-security multiverse
    # deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
  
