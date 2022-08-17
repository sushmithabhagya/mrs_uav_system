# MRS Gazebo Simulation
![](.fig/thumbnail.jpg)

| Simulation build status | [![Build Status](https://github.com/ctu-mrs/simulation/workflows/Melodic/badge.svg)](https://github.com/ctu-mrs/simulation/actions) | [![Build Status](https://github.com/ctu-mrs/simulation/workflows/Noetic/badge.svg)](https://github.com/ctu-mrs/simulation/actions) |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|

## Submodules

| ROS Package                                                                           | 18.04                                                                                                                                                                 | 20.04                                                                                                                                                                |
|---------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [mrs_simulation](https://github.com/ctu-mrs/mrs_simulation)                           | [![Build Status](https://github.com/ctu-mrs/mrs_simulation/workflows/Melodic/badge.svg)](https://github.com/ctu-mrs/mrs_simulation/actions)                           | [![Build Status](https://github.com/ctu-mrs/mrs_simulation/workflows/Noetic/badge.svg)](https://github.com/ctu-mrs/mrs_simulation/actions)                           |
| [mrs_gazebo_common_resources](https://github.com/ctu-mrs/mrs_gazebo_common_resources) | [![Build Status](https://github.com/ctu-mrs/mrs_gazebo_common_resources/workflows/Melodic/badge.svg)](https://github.com/ctu-mrs/mrs_gazebo_common_resources/actions) | [![Build Status](https://github.com/ctu-mrs/mrs_gazebo_common_resources/workflows/Noetic/badge.svg)](https://github.com/ctu-mrs/mrs_gazebo_common_resources/actions) |
| [px4](https://github.com/ctu-mrs/px4_firmware)                                        | [![Build Status](https://github.com/ctu-mrs/px4_firmware/workflows/Melodic/badge.svg)](https://github.com/ctu-mrs/px4_firmware/actions)                               | [![Build Status](https://github.com/ctu-mrs/px4_firmware/workflows/Noetic/badge.svg)](https://github.com/ctu-mrs/px4_firmware/actions)                               |
| [mavlink_sitl_gazebo](https://github.com/ctu-mrs/px4_sitl_gazebo)                     |                                                                                                                                                                       |                                                                                                                                                                      |

## System requirements

Required OS is Ubuntu 20.04 LTS 64-bit (Ubuntu 18.04 LTS 64-bit) or its flavors that can install ROS Noetic (ROS Melodic).
The suggested variant of OS installation is dual boot instead of virtualization that can be slow and can not handle well the simulation GUI.
We use [Gitman](https://github.com/jacebrowning/gitman) to manage the repository **submodules**.
The repository are supposed to be compiled by [catkin tools](https://catkin-tools.readthedocs.io).

## Unmanned Aerial Vehicles

| Model        | Spawn argument | Simulation                    |
|--------------|----------------|-------------------------------|
| DJI f330     | `--f330`       | ![](.fig/f330_simulation.jpg) |
| DJI f450     | `--f450`       | ![](.fig/f450_simulation.jpg) |
| Holybro x500 | `--x500`       | ![](.fig/x500_simulation.jpg) |
| DJI f550     | `--f550`       | ![](.fig/f550_simulation.jpg) |
| Tarot t650   | `--t650`       | ![](.fig/t650_simulation.jpg) |
| NAKI II      | `--naki`       | ![](.fig/naki_simulation.jpg) |

## Examples of tmuxinator simulation sessions

Selected tmuxinator scripts:

- [example_tmux_scripts/one_drone_gps](example_tmux_scripts/one_drone_gps)
- [example_tmux_scripts/one_drone_gps_standalone](example_tmux_scripts/one_drone_gps_standalone)
- [example_tmux_scripts/one_drone_optic_flow](example_tmux_scripts/one_drone_optic_flow)
- [example_tmux_scripts/two_drones_gps](example_tmux_scripts/two_drones_gps)

Bare tmux script (similar to the one used on real UAVs):

- [example_tmux_scripts/just_flying_bare_tmux](example_tmux_scripts/just_flying_bare_tmux)

For detail description of script capabilities for spawning vehicles see [mrs_simulation](https://github.com/ctu-mrs/mrs_simulation).

## Installing simulation

Install the whole [MRS UAV system](https://github.com/ctu-mrs/mrs_uav_system).

## Finishing your .bashrc

The `install.sh` script will add the following to your .bashrc:
```bash
source /opt/ros/<ros_version>/setup.bash
source /usr/share/gazebo/setup.sh
```

## UPDATE BY SUSHMITHA BHAGYA (sushmithabhagya27@gmail.com)

# Formation Control with Obstacle Avoidance for Team of Unmanned Aerial Vehicles in Forestry Robotics Applications
![image1](https://user-images.githubusercontent.com/109359404/183971029-e006f5cd-e4b3-4088-b010-5fbbb5c0e968.png)
Sushmitha Bhagya Sashi (sushmithabhagya27@gmail.com)

# Unmanned Aerial Vehicle

![UAVF550](https://user-images.githubusercontent.com/109359404/183973699-df7a3ea0-aa6c-4d1b-917a-c2cdda494319.png)

# System properties

- The platform iS built using Robot Operating System (Melodic, Noetic),ROS(2)
# Installation Steps

##### Step 1 : Set up Gazebo simulation forestry environment
To install Gazebo, run 
`curl -sSL http://get.gazebosim.org | sh` in your terminal
Test your installation by running the command `gazebo` on your terminal to make sure the simulator launches with no errors. If everything is fine, you can then just run CTRL+C in the terminal and proceed to the next step

##### Step 2  : Setting up and using forest models
`git clone https://bitbucket.org/semfire-isr-uc/semfire_gazebo_simulator.git`
- From inside the repository, run the following command to copy the Models folder to the .gazebo folder:

`cp -r Models ~/.gazebo`

- add that path to your .bashrc with:

`GAZEBO_MODEL_PATH=~/.gazebo/Models$GAZEBO_MODEL_PATH' >> ~/.bashrc`

#### Step 3 : Automatic Installation of MRS_UAV Package

```
sudo apt install lsb-core gnupg
cd /tmp
echo '
GIT_PATH=~/git
mkdir -p $GIT_PATH
cd $GIT_PATH
sudo apt -y install git
git clone https://github.com/ctu-mrs/mrs_uav_system
cd mrs_uav_system
git checkout master
git pull
./install.sh -g $GIT_PATH
source ~/.bashrc' > clone.sh && source clone.sh
```

This installation script will set everything up:

- install https://semfire-core.slite.page/app/docs/gJT6gbaOu_;

- install other dependencies such as git, gitman, etc.;

- clone uav_core, simulation, example_ros_packages into ~/git;

- install more dependencies such as tmux and tmuxinator;

- create ros workspace in ~/mrs_workspace for the uav_core and simulation;

- create a ros workspace in ~/workspace for examples;

- link packages to the workspaces;

- compile the workspaces;

- added configuration lines into your ~/.bashrc.


## Modifications 

I have made modifications in `~/formation_workspace/src/simulation/example_tmux_scripts/one_drone_gps & ~/formation_workspace/src/simulation/example_tmux_scripts/three_drone_gps` inorder to run it with f550

##### Step 1
 Copy the required .world files from semfire_gazebo_simulator to the MRS UAV Sytem
 `cp -r low-density-forest-30by30.world ~/formation_workspace/src/simulation/ros_packages/mrs_gazebo_common_resources/worlds`
 
##### Step 2 
Create a new pos.yaml file and copy below specifications and save inside ~/formation_workspace/src/simulation/example_tmux_scripts/one_drone_gps
```
uav1:
  id: 1
  x: -20 
  y: 1
  z: 1
  heading: 1
  ```

{This specification is used to spawn the UAV Outside of the simulated forest}

##### Step 3
Open the session.yaml file from ~/formation_workspace/src/simulation/example_tmux_scripts/one_drone_gps
`nano session.yaml`

#### Step 4: Edit the below parameters
- Change the UAV type to `UAV_TYPE=f550`
- Change the world simulation to `world_name:=low-density-forest-30by30`
- Use below command for spawning the uav with required sensor and pos file
`rosservice call /mrs_drone_spawner/spawn "1 f550 --enable_rangefinder --enable_realsense_front --pos_file `pwd`/pos.yaml"`

#### Run the Simulation
`./start.sh`

#### Same steps can be followed for the simulation of three_drone_gps
 
