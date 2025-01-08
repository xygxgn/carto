## Cartographer

### Prerequisites
- **System**
  - Ubuntu 20.04
  - ROS Noetic
- **Libraries**
  * `sudo apt-get install -y python3-wstool python3-rosdep ninja-build stow`

- **ceres-solver**
  * `sudo apt-get install liblapack-dev libsuitesparse-dev libgflags-dev libgoogle-glog-dev libgtest-dev libcxsparse3 -y`
  * `cd ~/Documents/`
  * `git clone -b 1.14.0 https://gitee.com/xygxgn/ceres-solver.git`
  * `cd ceres-solver`
  * `mkdir build && cd build`
  * `cmake ..`
  * `sudo make install -j8`

### Build
  * *(with this package)*
  * `mkdir -p ~/catkin_ws/src/ && cd ~/catkin_ws/src/`
  * `git clone https://gitee.com/xygxgn/cartographer.git`
  * `cd cartographer`
  * `rosdep install --from-paths src --ignore-src --rosdistro=$ROS_DISTRO -y`
  * `src/cartographer/scripts/install_abseil.sh`
  * `pip3 install --upgrade Sphinx`
  * `catkin_make_isolated --install --use-ninja`
  * *(optional)* `echo "source ~/catkin_ws/src/carto/devel_isolated/setup.bash" >> ~/.bashrc`

  * *(without this package)*
  * `mkdir -p ~/catkin_ws/src/carto/src/ && cd ~/catkin_ws/src/carto/src`
  * `git clone https://github.com/cartographer-project/cartographer.git`
  * `git clone https://github.com/cartographer-project/cartographer_ros.git`
  * `cd ..`
  * `wstool init src`
  * `wstool merge -t src https://raw.githubusercontent.com/cartographer-project/cartographer_ros/master/cartographer_ros.rosinstall`
  * `wstool update -t src`
  * `gedit cartographer/package.xml`
  * commit `<depend>libabsl-dev</depend>`
  * `rosdep install --from-paths src --ignore-src --rosdistro=$ROS_DISTRO -y`
  * `src/cartographer/scripts/install_abseil.sh`
  * `catkin_make_isolated --install --use-ninja`
  * *(optional)* `echo "source ~/catkin_ws/src/carto/devel_isolated/setup.bash" >> ~/.bashrc`

### Run
  * `source install_isolated/setup.bash`
  * `wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag`
  * `roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag`


If you find this work useful or interesting, please kindly give us a star :star:, thanks!


