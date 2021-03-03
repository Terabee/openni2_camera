# ROS openni 2.0 wrapper for Terabee depth cameras

This package is a modified version of the openni2_camera package, it has been updated to work with QQQVGA (80x60 pixels) cameras.

## Install the pre-required ROS packages

* For Ubuntu 16.04 with ROS Kinetic
```
$ sudo apt-get install ros-kinetic-rgbd-launch
```
* For Ubuntu 14.04 with ROS Indigo
```
$ sudo apt-get install ros-indigo-rgbd-launch
```

## Install openni2 packages for Ubuntu
Please install the openni2 package using the following command:
```
$ sudo apt-get install libopenni2-0 libopenni2-dev
```

## Download and install the Terabee 3Dcam SDK
You can download the Terabee SDK from the Downloads section of Terabee 3Dcam [here](https://www.terabee.com/shop/3d-tof-cameras/terabee-3dcam/).

Then install it using the following commands:
```
$ tar -xzf TERABEE-Linux-x64-OpenNI2.2.tar.gz
$ cd TERABEE-Linux-x64-OpenNI2.2
$ sudo ./install.sh
```

### Install OpenCV 2

In order to use the SDK, it is **mandatory** to install the right OpenCV version. We recommend following the OpenCV installation for linux available [here](https://github.com/Terabee/linux_openni2_samples#install-opencv).

# Build and use the modified openni2_camera package
## Downloading and building the package

 To clone and build the package in your workspace follow these steps:

```
cd ~/ros_ws/src
git clone https://github.com/Terabee/openni2_camera.git
cd ~/ros_ws
catkin_make
source devel/setup.bash
```
## Launching the OpenNI2 driver

After your workspace is built and sourced, you can launch the openni2 package to start the camera driver. Please make sure that the Terabee 3Dcam is connected then run the following command:
```
roslaunch openni2_launch Terabee_3Dcam.launch
```

## Visualize depth and IR images
Once the driver is running, you will be able to see the camera output using ROS visualization tools.

### Using rqt with the "Image View" plugin

Launch rqt using the following command:
```
$ rqt
```

Then load the "Image View" plugin located in Plugins>Visualization and select one of the following topics:
* */camera/depth/image* to visualize depth
* */camera/ir/image* to visualize IR frame


### Using the *image_view* node directly

* To view the Depth image, run the following command:
```
$ rosrun image_view image_view image:=/camera/depth/image
```
* To view the IR image, run the following command:
```
$ rosrun image_view image_view image:=/camera/ir/image
```
