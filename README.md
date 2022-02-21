# PX4 ROS Gazebo simulation

PX4 toolchain development environment setup for drone simulations in Gazebo and ROS


# Commands used 

    sudo apt update
    sudo apt upgrade
    sudo apt install git
    mkdir src
    cd src
    git clone https://github.com/PX4/Firmware.git --recursive
    cd Firmware
    bash ./Tools/setup/ubuntu.sh
    
Reboot computer

    wget https://raw.githubusercontent.com/ktelegenov/sim_ros_setup_noetic/main/ubuntu_sim_ros_noetic.sh
    bash ubuntu_sim_ros_noetic.sh

Close the terminal and open it again

    cd src/Firmware
    git submodule update --init --recursive
    DONT_RUN=1 make px4_sitl_default gazebo

    source Tools/setup_gazebo.bash $(pwd) $(pwd)/build/px4_sitl_default
    export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd):$(pwd)/Tools/sitl_gazebo

    roslaunch px4 multi_uav_mavros_sitl.launch
