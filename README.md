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

I have made modifications in `~/mrs_workspace/src/simulation/example_tmux_scripts/one_drone_gps & ~/mrs_workspace/src/simulation/example_tmux_scripts/three_drone_gps` inorder to run it with f550 uav type.

##### Step 1
 Copy the required .world files from semfire_gazebo_simulator to the MRS UAV Sytem
 
 `cp -r low-density-forest-30by30.world ~/mrs_workspace/src/simulation/ros_packages/mrs_gazebo_common_resources/worlds`
 
##### Step 2 
Create a new pos.yaml file. You can specify the initial position of drone in simulation using --pos_file parameter

```
cd  ~/mrs_workspace/src/simulation/example_tmux_scripts/one_drone_gps
nano pos.yaml
```
Copy below parameters to the newly created yaml file.
```
uav1:
  id: 1
  x: -20 
  y: 1
  z: 1
  heading: 1
 ```

{The Negative value for x is used to spawn the UAV outside of the simulated forest}

##### Step 3
Open the session.yaml file from your workspace
```
cd ~/your_workspace/src/simulation/example_tmux_scripts/one_drone_gps
nano session.yaml
```

#### Step 4: Edit the below parameters
- Change the UAV type to f550 and edit the UAV_NAME as shown below

`pre_window: export UAV_NAME=uav1; export RUN_TYPE=simulation; export UAV_TYPE=f550; export WORLD_NAME=simulation; export SENSORS="garmin_down"

- Change the world files. You can choose any .world files, for example

`- waitForRos; roslaunch mrs_simulation simulation.launch world_name:=low-density-forest-30by30 gui:=true`

- Use below command for spawning the uav with required sensor and pos file
`rosservice call /mrs_drone_spawner/spawn "1 f550 --enable_rangefinder --enable_realsense_front --pos_file `pwd`/pos.yaml" `

#### Run the Simulation

`./start.sh`

![image](https://user-images.githubusercontent.com/111078976/190230907-292d1dc0-9470-4769-91e7-bab6efaca5db.png)


#### Step 5: Spawning Three drones
- three_drone_gps is the folder used for spawning three UAVs. Above mentioned steps can be followed for the simulation of three_drone_gps with few additional changes. In the below code of session.yaml file the values for “i” is assigned with 1 to 3 for 3 UAVs and we can spawn upto n UAVs simply by changing the value of n.

`on_project_start: nums=$(shuf -i 1-3 -n 3 | tr '\n' " "); echo "UAV_NUMBERS=($nums)" > /tmp/random_uav_numbers`

- We have to make sure we are launching the status for three uavs, by editing the below step
```
 panes:
        - export UAV_NAME="uav${UAV_NUMBERS[1]}"; waitForSimulation; roslaunch mrs_uav_status status.launch
        - export UAV_NAME="uav${UAV_NUMBERS[2]}"; waitForSimulation; roslaunch mrs_uav_status status.launch
        - export UAV_NAME="uav${UAV_NUMBERS[3]}"; waitForSimulation; roslaunch mrs_uav_status status.launch
 panes:
        - export UAV_NAME="uav${UAV_NUMBERS[1]}"; waitForOdometry; roslaunch mrs_uav_general core.launch
        - export UAV_NAME="uav${UAV_NUMBERS[2]}"; waitForOdometry; roslaunch mrs_uav_general core.launch
        - export UAV_NAME="uav${UAV_NUMBERS[3]}"; waitForOdometry; roslaunch mrs_uav_general core.launch
```
- By using a single pos.yaml file, we can position the UAVs anywhere in the simulated forest. Below table shows the pos.yaml configurations to spawn the three UAVS at different x-locations.

| UAV1  | UAV2  | UAV3  |
|-------|-------|-------|
| id: 1 | id: 1 | id: 1 |
| x: -10| x: -15| x: -20|
| y: 1  | y: 1  | y: 1  |
| z: 1  | z: 1  | z: 1  |

#### Run the Simulation

`./start.sh`

Three UAVs will be spawned in three different positions and rosservice can be used to give different trajectories here

![image](https://user-images.githubusercontent.com/111078976/190230826-3c57cb0d-556e-479b-9592-661a4d65459a.png)


 
