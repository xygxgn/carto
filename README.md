## Cartographer

### Prerequisites
- **System**
  - Ubuntu 22.04
  - ROS Humble
- **Libraries**
  * `sudo apt-get install libceres-dev python3-wstool python3-rosdep ninja-build stow -y`

### Build
  * *(with this package)*
  * `mkdir -p ~/colcon_ws/src/ && cd ~/colcon_ws/src/`
  * `git clone -b humble https://gitee.com/xygxgn/carto.git`
  * `cd carto`
  * `rosdep install --from-paths src --ignore-src --rosdistro=$ROS_DISTRO -y`
  * `colcon build --packages-up-to cartographer_ros`
  * *(optional)* `echo "source ~/colcon_ws/src/carto/install/setup.bash" >> ~/.bashrc`

  * *(without this package)*
  * `mkdir -p ~/colcon_ws/src/carto/src/ && cd ~/colcon_ws/src/carto/src`
  * `git clone -b ros2 https://github.com/ros2/cartographer.git`
  * `git clone -b ros2 https://github.com/ros2/cartographer_ros.git`
  * `cd ..`
  * `rosdep install --from-paths src --ignore-src --rosdistro=$ROS_DISTRO -y`
  * `colcon build --packages-up-to cartographer_ros`
  * *(optional)* `echo "source ~/colcon_ws/src/carto/install/setup.bash" >> ~/.bashrc`

### Run
  * `source install/setup.bash`
  * `wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag`
  * `pip3 install rosbags`
  * `rosbags-convert --src ~/Downloads/cartographer_paper_deutsches_museum.bag --dst ~/Downloads/cartographer_paper_deutsches_museum`
  * `ros2 launch cartographer_ros demo_backpack_2d.launch.py bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum/cartographer_paper_deutsches_museum.db3`


If you find this work useful or interesting, please kindly give us a star :star:, thanks!


