# Dataset description

This document describes the rosbag datasets used to generate the results reported in the manuscript.

## Dataset access

Repository URL:

> **[Dataset URL](https://irtacat-my.sharepoint.com/:f:/g/personal/marc_felip_irta_cat/IgDFIjUl8ma1TJKj7rw3kUrRASQ7X8_j5jnBlEXROTZm8Qc?e=YG3FgY)**


## Dataset summary

| Dataset ID | LiDAR | Trajectory type | Replicate | Rosbag file | Approx. duration [s]|
|---|---|---|---:|---|---:|
| ous_ss_01 | Ouster OS0-128 | Single-side | 1 | `ous_ss_01.bag` | `93` |
| ous_ss_02 | Ouster OS0-128 | Single-side | 2 | `ous_ss_02.bag` | `96` |
| ous_ss_03 | Ouster OS0-128 | Single-side | 3 | `ous_ss_03.bag` | `94` |
| ous_rt_01 | Ouster OS0-128 | Round-trip | 1 | `ous_ss_01.bag` | ` 181` |
| ous_rt_02 | Ouster OS0-128 | Round-trip | 2 | `ous_ss_02.bag` | `190` |
| ous_rt_03 | Ouster OS0-128 | Round-trip | 3 | `ous_ss_03.bag` | `179` |
| lvx_ss_01 | Livox Mid-360 | Single-side | 1 | `lvx_ss_01.bag` | `92` |
| lvx_ss_02 | Livox Mid-360 | Single-side | 2 | `lvx_ss_02.bag` | `103` |
| lvx_ss_03 | Livox Mid-360 | Single-side | 3 | `lvx_ss_03.bag` | `92` |
| lvx_rt_01 | Livox Mid-360 | Round-trip | 1 | `lvx_rt_01.bag` | `181` |
| lvx_rt_02 | Livox Mid-360 | Round-trip | 2 | `lvx_rt_02.bag` | `197` |
| lvx_rt_03 | Livox Mid-360 | Round-trip | 3 | `lvx_rt_03.bag` | `178` |



## ROS topics

The following topic names are expected by the configuration files provided in this repository:

| Sensor setup | Point cloud topic | IMU topic | 
|---|---|---|
| Ouster OS0-128 | `ouster/points` | `imu_correct` | 
| Livox Mid-360 | `livox/lidar` | `imu_correct` | 

The following topic names are 


## Data reuse notes

- The rosbags are provided to support reproducibility of the orchard reconstruction results.
- The data should be used together with the configuration files in this repository and the original LIO-SAM implementation.