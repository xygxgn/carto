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
  * `mv ceres-solver ceres-solver-1.14.0`
  * `cd ~/Documents/ceres-solver-1.14.0`
  * `mkdir build && cd build`
  * `cmake ..`
  * `sudo make install -j8`

### Build
  * *(with this package)*
  * `git clone https://giteecom/xygxgn/cartographer.git`
  * `cd cartographer`
  * `wstool init src`
  * `wstool merge -t src https://raw.githubusercontent.com/cartographer-project/cartographer_ros/master/cartographer_ros.rosinstall`
  * `wstool update -t src`
  * `rosdep install --from-paths src --ignore-src --rosdistro=noetic -y`
  * `src/cartographer/scripts/install_abseil.sh`
  * `catkin_make_isolated --install --use-ninja`
  * `source install_isolated/setup.bash`

  * *(without this package)*
  * `mkdir -p ~/cartographer/src/ && cd ~/cartographer/src/`
  * `git clone https://github.com/cartographer-project/cartographer.git`
  * `git clone https://github.com/cartographer-project/cartographer_ros.git`
  * `sudo apt-get install -y python3-wstool python3-rosdep ninja-build stow`
  * `wstool init src`
  * `wstool merge -t src https://raw.githubusercontent.com/cartographer-project/cartographer_ros/master/cartographer_ros.rosinstall`
  * `wstool update -t src`
  * `gedit cartographer/package.xml`
  * commit `<depend>libabsl-dev</depend>`
  * `rosdep install --from-paths src --ignore-src --rosdistro=noetic -y`
  * `src/cartographer/scripts/install_abseil.sh`
  * `catkin_make_isolated --install --use-ninja`
  * `source install_isolated/setup.bash`

### Run
  * `wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag`
  * `roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag`


If you find this work useful or interesting, please kindly give us a star :star:, thanks!


