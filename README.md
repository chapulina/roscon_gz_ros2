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

Press the play button on the top, or `F5` to start the presentation.

## Demos

This presentation / simulation contains demos of 14 different plugins from the
`gazebo_plugins` package. Each demo has its own slide. Click on the arrow to
open a dialog with information about the plugin.

You can also skip directly to the demos by typing the slide number on the top
box:

Plugin | Slide
-- | --
`gazebo_ros_camera` | 34
`gazebo_ros_diff_drive` | 35
`gazebo_ros_video` | 36
`gazebo_ros_gps_sensor` | 43
`gazebo_ros_imu_sensor` | 44
`gazebo_ros_force` | 45
`gazebo_ros_bumper` | 46
`gazebo_ros_ray` | 47
`gazebo_ros_joint_state_publisher` | 48
`gazebo_ros_joint_pose_trajectory` | 49
`gazebo_ros_projector` | 50
`gazebo_ros_planar_move` | 51
`gazebo_ros_hand_of_god` | 52
`gazebo_ros_vacuum_gripper` |

## Performance

If the simulation is laggy, it's probably the large heightmap causing low FPS.
If that's the case, you can try:

* Setting the heightmap level of detail on `~/.gazebo/gui.ini`:

    ~~~
    [heightmap]
    lod=3
    ~~~

* Lowering the resolution of your monitor :smile:

* Comment out the heightmap from the SDF file :grimacing:

