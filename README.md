# Robot side demo notes

## Demo launch commands

### On the left machine

`rosrun julia_main save_ears.sh`

`rosrun baxter_tools enable_robot.py -e`

`roslaunch simtrack_nodes camera_kinect.launch`

`roslaunch simtrack_nodes julia_vision.launch`

`roslaunch julia_main lemon_detection.launch`

### On the right machine

`roslaunch julia_main planning.launch`

`roslaunch julia_main command_listener.launch`

### Test commands

(Remember to shut down the voice server for the demo because the vision side will launch the same server.)    
`rosrun voice_server voice.py`

`rostopic pub /robot_cmd std_msgs/String "pour('rvs_orangenakedbottle-exported',1)"`

`rostopic pub /robot_cmd std_msgs/String "pour('rvs_whitenakedbottle1-exported',1)"`

`rostopic pub /robot_cmd std_msgs/String "serve()"`

`rostopic pub /robot_cmd std_msgs/String "put('lemon', 1)"`

`rostopic pub /robot_cmd std_msgs/String "put('lime', 1)"`

## Setup the physical objects

Place the lemon/lime tray and the mixing jar overlapping the corresponding obstacle box in the planning scene

<img src="https://github.com/YZHANGFPE/demo_instructions/blob/master/figures/mixingBottle.jpg" width="500">

Naked bottle setup1

<img src="https://github.com/YZHANGFPE/demo_instructions/blob/master/figures/setup1.jpg" width="500">

Naked bottle setup2

<img src="https://github.com/YZHANGFPE/demo_instructions/blob/master/figures/setup2.jpg" width="500">

## Calibration

### Step 1 
Follow the "extrinsic calibration" instruction in the repository
https://github.com/YZHANGFPE/kinect_calibration

<img src="https://github.com/YZHANGFPE/demo_instructions/blob/master/figures/tagLocation.jpg" width="500">

the calibration file is save in the directory kinect_calibration/config/base_camera_tf.yaml

### Step 2
Manually check the overlap of the pointcloud and the robot model; Either move the camera or change the calibration file to correct the differences. 

<img src="https://github.com/YZHANGFPE/demo_instructions/blob/master/figures/checkCalibration.jpg" width="500">

On the left machine

`roslaunch simtrack_nodes camera_kinect.launch`
`roslaunch simtrack_nodes julia_vision.launch`

On the right machine

`roslaunch julia_main planning.launch`

## Misc
### Steps to boot up the left machine
Boot into the recovery mode and resume

### Instructions to fix the login issue on the right machine
1. Boot into the recovery mode and resume
2. At the login screen, press `CTRL + ALT + F3`
3. `sudo service lightdm stop`
4. Install the NVIDIA driver. The file is at the root directory. 
5. `sudo service lightdm start`
6. `CTRL + ALT + F7`
