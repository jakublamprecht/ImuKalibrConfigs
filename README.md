# Kalibr config files

## Overview

In this repo we included configuration files for Econtara camera, checkerboard calibration reference target and the following IMUs:

* XSens 
* Microstrain 3DM-GX4-25
* ADIS
* Some low cost IMU
* Phone IMU

## Data used in YAML files

* For camera YAML file we used data found at [this site](https://www.e-consystems.com/3D-USB-stereo-camera.asp) and [this YAML file](#)
* For calibration target we measured required information and followed template provided in Kalibrs documentation
* For XSens IMU we used the documentation included with the IMU and [this website](https://www.xsens.com/products/mti/)
* For Microstrain we used following [specification](http://www.microstrain.com/inertial/3dm-gx4-25)
* For ADIS we used file provided at [Kalibr's github site](https://github.com/ethz-asl/kalibr/wiki/downloads)
* For Low cost imu we used exactly the same data as in ADIS YAML file
* For Phone IMU we used data provided at this [site](https://www.invensense.com/wp-content/uploads/2015/03/DS-000081-v1.01.pdf) random_walk values are taken from configuration file for ADIS

## How to run

* For one IMU:

* For multiple IMUs:

```bash
kalibr_calibrate_imu_camera --cam cam_econtara.yaml --target checkerboard.yaml --imu imu_configs/imu_xsens.yaml imu_configs/imu_microstrain.yaml imu_configs/imu_adis.yaml imu_configs/imu_lowcost.yaml --imu-models --bag ${someNameOfBag}.bag
```

## Issues

For multiple IMUs calibration it might be neccessary to add `calibrated` keyword for each IMU after `--imu-models`:

```bash
kalibr_calibrate_imu_camera --cam cam_econtara.yaml --target checkerboard.yaml --imu imu_configs/imu_xsens.yaml imu_configs/imu_microstrain.yaml imu_configs/imu_adis.yaml imu_configs/imu_lowcost.yaml --imu-models calibrated calibrated calibrated calibrated--bag ${someNameOfBag}.bag
```

## Results

Calibration results in a file that contains data required to calculate differences in position and orientation between IMUs. This allows us to relate data from all IMUs to the coordinate system of one of the IMUs.

## Links

* [Link to Kalibr documentation](https://github.com/ethz-asl/kalibr/wiki)
* [How to install](https://github.com/ethz-asl/kalibr/wiki/installation)
* [How to create YAML files for camera and IMUs](https://github.com/ethz-asl/kalibr/wiki/yaml-formats)
* [Calibration targets docs](https://github.com/ethz-asl/kalibr/wiki/calibration-targets)
* How to run the calibration for [single IMU](https://github.com/ethz-asl/kalibr/wiki/camera-imu-calibration) and [multiple IMUs](https://github.com/ethz-asl/kalibr/wiki/Multi-IMU-and-IMU-intrinsic-calibration)

