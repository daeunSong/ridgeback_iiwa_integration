# Ridgeback + iiwa Integration

*Tested on **Ubuntu 18.04** with **ROS Melodic**.*

<img src="./doc/img/demo.png" width="600">

This repository provides our customed ridgeback integration with KUKA LBR iiwa 7 R800 based on [ridgeback_manipulation](https://github.com/ridgeback/ridgeback_manipulation). 


## Installation

1. Clone [iiwa_stack](https://github.com/daeunSong/iiwa_stack/tree/glab/drawing) and [iiwa_stack_examples](https://github.com/daeunSong/iiwa_examples) repositories to your workspace:
  ```sh
  mkdir ridgeback_iiwa_ws && cd ridgeback_iiwa_ws && mkdir src
  catkin_init_workspace
  cd src
  git clone https://github.com/daeunSong/iiwa_stack/tree/glab/drawing.git
  git clone --recursive https://github.com/daeunSong/iiwa_examples.git
  ```

2. Clone [ridgeback](https://github.com/daeunSong/ridgeback/tree/glab/integration), [ridgeback_simulator](https://github.com/daeunSong/ridgeback_simulator/tree/glab/integration), [ridgeback_iiwa_integration](https://github.com/daeunSong/ridgeback_iiwa_integration/tree/devel) repositories to your workspace:
  ```sh
  git clone https://github.com/daeunSong/ridgeback/tree/glab/integration.git
  git clone https://github.com/daeunSong/ridgeback_simulator/tree/glab/integration.git
  git clone https://github.com/daeunSong/ridgeback_iiwa_integration/tree/devel.git
  ```

3. Install the dependencies:
  ```sh
  cd ..
  rosdep install --from-paths src --ignore-src -r -y
  ```

4. Add a following line in ~/.bashrc:

  `export RIDGEBACK_URDF_EXTRAS=$(catkin_find ridgeback_iiwa_description urdf/ridgeback_iiwa_7_description.urdf.xacro --first-only)`

5. Build the workspace:
  ```sh
  catkin build
  ```

6. Source the workspace:
  ```sh
  source devel/setup.bash
  ```
   You can also add this line in ~/.bashrc, but be aware that this has to be above the line in step 4.


## Demo
Run the following commands in respective terminals:
```sh
roslaunch ridgeback_gazebo ridgeback_world.launch
roslaunch ridgeback_navigation odom_navigation_demo.launch
roslaunch ridgeback_viz view_robot.launch config:=navigation
```
```sh
roslaunch ridgeback_iiwa_moveit_config demo.launch
```
