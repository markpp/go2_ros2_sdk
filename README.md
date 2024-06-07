![Ros2 SDK](https://github.com/abizovnuralem/go2_ros2_sdk/assets/33475993/49edebbe-11b6-49c6-b82d-bc46257674bd)

# Welcome to the Unitree Go2 ROS2 SDK Project!

[![IsaacSim](https://img.shields.io/badge/IsaacSim-4.0-silver.svg)](https://docs.omniverse.nvidia.com/isaacsim/latest/overview.html)
[![Python](https://img.shields.io/badge/python-3.10-blue.svg)](https://docs.python.org/3/whatsnew/3.10.html)
[![Linux platform](https://img.shields.io/badge/platform-linux--64-orange.svg)](https://releases.ubuntu.com/22.04/)
[![Windows platform](https://img.shields.io/badge/platform-windows--64-orange.svg)](https://www.microsoft.com/en-us/)
![ROS2 Build](https://github.com/abizovnuralem/go2_ros2_sdk/actions/workflows/ros_build.yaml/badge.svg)
[![License](https://img.shields.io/badge/license-BSD--2-yellow.svg)](https://opensource.org/licenses/BSD-2-Clause)

We are happy to present you our integration of the Unitree Go2 with ROS2 over Wi-Fi, that was designed by the talented [@tfoldi](https://github.com/tfoldi). You can explore his groundbreaking work at [go2-webrtc](https://github.com/tfoldi/go2-webrtc).

This repo will empower your Unitree GO2 AIR/PRO/EDU robots with ROS2 capabilities, using both WebRTC (Wi-Fi) and CycloneDDS (Ethernet) protocols.

## Project RoadMap:

1. URDF :white_check_mark: 
2. Joint states sync in real time :white_check_mark: 
3. IMU sync in real time :white_check_mark: 
4. Joystick control in real time :white_check_mark: 
6. Go2 topics info in real time :white_check_mark: 
7. Foot force sensors info in real time :white_check_mark: 
8. Lidar stream (added pointCloud2) :white_check_mark: 
9. Camera stream :white_check_mark:
10. Foxglove bridge :white_check_mark:
11. Laser Scan :white_check_mark:
12. SLAM (slam_toolbox) :white_check_mark:
13. Navigation (nav2) :white_check_mark:
14. Multi robot support :white_check_mark:
15. WebRTC and CycloneDDS support :white_check_mark:
16. Creating a PointCloud map and store it
17. Object detection
18. AutoPilot

## Your feedback and support mean the world to us. 

If you're as enthusiastic about this project as we are, please consider giving it a :star: star. 

Your encouragement fuels our passion and helps us develop our RoadMap further. We welcome any help or suggestions you can offer!

Together, let's push the boundaries of what's possible with the Unitree Go2 and ROS2!

## Exciting Features:

:sparkles: Full ROS2 SDK support for your Unitree GO2

:robot: Compatible with AIR, PRO, and EDU variants

:footprints: Access to foot force sensors feedback (available on some GO2 PRO models or EDU)


## Real time Go2 Air/PRO/EDU joints sync:

<p align="center">
<img width="1280" height="640" src="https://github.com/abizovnuralem/go2_ros2_sdk/assets/33475993/bf3f5a83-f02b-4c78-a7a1-b379ce057492" alt='Go2 joints sync'>
</p>

## Go2 Air/PRO/EDU lidar point cloud:

<p align="center">
<img width="1280" height="640" src="https://github.com/abizovnuralem/go2_ros2_sdk/assets/33475993/9c1c3826-f875-4da1-a650-747044e748e1" alt='Go2 point cloud'>
</p>


## SLAM and Camera stream

<p align="center">
<img width="1280" height="640" src="https://github.com/abizovnuralem/go2_ros2_sdk/assets/33475993/59f33599-a54c-4cff-8ac2-6859a05ccb8a" alt='Slam'>
</p>


## System requirements
Tested systems and ROS2 distro
|systems|ROS2 distro|Build status
|--|--|--|
|Ubuntu 22.04|iron|![ROS2 CI](https://github.com/abizovnuralem/go2_ros2_sdk/actions/workflows/ros_build.yaml/badge.svg)
|Ubuntu 22.04|humble|![ROS2 CI](https://github.com/abizovnuralem/go2_ros2_sdk/actions/workflows/ros_build.yaml/badge.svg)
|Ubuntu 22.04|rolling|![ROS2 CI](https://github.com/abizovnuralem/go2_ros2_sdk/actions/workflows/ros_build.yaml/badge.svg)


## Installation

clone this repo to src folder of your own ros2_ws folder

```
git clone --recurse-submodules https://github.com/abizovnuralem/go2_ros2_sdk.git

cd go2_ros2_sdk
sudo apt install python3-pip clang
pip install -r requirements.txt
cd ..
mkdir -p ros2_ws/src
copy all files from go2_ros2_sdk folder to ros2_ws/src folder

```
install rust language support in your system https://www.rust-lang.org/tools/install 

cargo should work in terminal
```
cargo --version
```

Build it

You need to install ros2 and rosdep package first.

https://docs.ros.org/en/humble/Installation.html


```
source /opt/ros/$ROS_DISTRO/setup.bash
cd ros2_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build
```

## Usage
don't forget to setup your GO2-robot in Wifi-mode and get IP then

```
cd ros2_ws
source install/setup.bash
export ROBOT_IP="robot_ip"
ros2 launch go2_robot_sdk robot.launch.py
```


## Multi robot support 

If you want to connect several robots for collaboration:
```
export ROBOT_IP="robot_ip_1, robot_ip_2, robot_ip_N"
```

## Switching between webrtc connection (Wi-Fi) to CycloneDDS (Ethernet)
```
export CONN_TYPE="webrtc"
or
export CONN_TYPE="cyclonedds"
```

## Foxglove

<p align="center">
<img width="1200" height="630" src="https://github.com/abizovnuralem/go2_ros2_sdk/assets/33475993/f0920d6c-5b7a-4718-b781-8cfa03a88095" alt='Foxglove bridge'>
</p>

To use Foxglove, you need to install Foxglove Studio:
```
sudo snap install foxglove-studio
```

1. Open Foxglove Studio and press "Open Connection".
2. In the "Open Connection" settings, choose "Foxglove WebSocket" and use the default configuration ws://localhost:8765, then press "Open".
3. (Optional) You can also import a default layout view from the foxglove.json file located inside this repository.


## Thanks

Special thanks to @tfoldi, @legion1581, @budavariam, @alex.lin and TheRoboVerse community!

## License

This project is licensed under the BSD 2-clause License - see the [LICENSE](https://github.com/abizovnuralem/go2_ros2_sdk/blob/master/LICENSE) file for details.
