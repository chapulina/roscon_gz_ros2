# The New Architecture of Gazebo Wrappers for ROS 2 @ ROSCon 2019

ROSCon 2019 presentation by Louise Poubel (@chapulina) and Jose Luis Rivero (@jrivero).

## Dependencies

* Gazebo 9
* ROS 2 Dashing
* [SimSlides](https://github.com/chapulina/simslides)
* [UAV testing](https://github.com/osrf/uav_testing)

## Build

1. Install the ROS Dashing as instructed [here](https://index.ros.org/doc/ros2/Installation/Linux-Install-Debians/).

1. Install `gazebo_ros_pkgs`, which also installs Gazebo:

        sudo apt install ros-dashing-gazebo-ros-pkgs

1. Build this package together with SimSlides:

        mkdir -p ws/src
        cd ws/src
        git clone https://github.com/chapulina/simslides -b master
        git clone https://github.com/chapulina/roscon_gz_ros2 -b master
        git clone https://github.com/osrf/uav_testing -b ros2_initial_port
        cd ..
        colcon build --packages-up-to roscon_gz_ros2

## Run

        . /usr/share/gazebo/setup.sh
        . ~/ws/install/setup.sh
        ros2 launch roscon_gz_ros2 roscon.launch.py verbose:=true

