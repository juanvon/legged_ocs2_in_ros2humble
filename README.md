# legged_ocs2_in_ros2humble

[zhengxiang94/ocs2_ros2](https://github.com/zhengxiang94/ocs2_ros2)
## Summary
OCS2_ROS2 is developed based on [OCS2](https://github.com/leggedrobotics/ocs2), and features that are not supported at the moment:

* ocs2_mpcnet
* ocs2_doc

## Installation
### Prerequisites
The OCS2 library is written in C++17. It is tested under Ubuntu 22.04 with library versions as provided in the package sources.

### Dependencies
* C++ compiler with C++17 support
* ros2 humble
* Eigen (v3.4)
* Boost C++ (v1.74)
* For rigid multi-body dynamics library and self collision support clone Pinocchio and HPP-FCL into your workspace
* RaiSim simulator can be used as a provider for rollouts. The corresponding ocs2_raisim package has additional requirements
```
sudo apt-get install ros-humble-grid-map-cv ros-humble-grid-map-msgs ros-humble-grid-map-ros ros-humble-grid-map-sdf libmpfr-dev libpcap-dev
```
* Pinocchio and hpp-fcl
```
# git clone pinocchio
git clone --recurse-submodules https://github.com/zhengxiang94/pinocchio.git
# git clone hpp-fcl
git clone --recurse-submodules https://github.com/zhengxiang94/hpp-fcl.git

# install hpp-fcl
cd hpp-fcl
mkdir build
cd build
cmake ..
make -j4
make install

# install pinocchio
cd pinocchio
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local
make -j4
make install
```
* Raisim
```
git clone --depth 1 https://github.com/raisimTech/raisimLib.git -b v1.1.01
sudo apt-get update && sudo apt-get install checkinstall
cd raisimLib
mkdir build
cd build
cmake .. -DRAISIM_EXAMPLE=ON -DRAISIM_PY=ON -DPYTHON_EXECUTABLE=$(python3 -c "import sys; print(sys.executable)")
make -j4
sudo checkinstall
```
* For various robotic assets used in OCS2 unit tests and the robotic examples
```
# Clone ocs2_robotic_assets in ros2_ws/src
git clone https://github.com/zhengxiang94/ocs2_robotic_assets.git
```
* plane_segmentation_ros2
```
# Clone plane_segmentation_ros2 in ros2_ws/src
git clone https://github.com/zhengxiang94/plane_segmentation_ros2.git
```
* ocs2_ros2
```
git clone https://github.com/zhengxiang94/ocs2_ros2.git
```
* colcon build
```
cd ros2_ws
colcon build
```

