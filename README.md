# NeuDepth
This is a main page of NeuDepth project. The project aim is the loosely coupled fusion of neural depth estimation (NDE) and SLAM.
We provide the estimation workflow that consists of two ROS2 packages: slam_deep_mapper and depth_map_optimizer. The description and installation guidelines visit
GitHub repos:  
[slam_deep_mapper](https://github.com/kubakolecki/slam_deep_mapper)  
[depth_map_optimizer](https://github.com/kubakolecki/depth_map_optimizer)

![My Image](NeuDepth.svg)

## General worflow description
The workflow consists of 2 ROS2 packages: [slam_deep_mapper](https://github.com/kubakolecki/slam_deep_mapper), [depth_map_optimizer](https://github.com/kubakolecki/depth_map_optimizer). Both of them depend on ROS2 custom messages, that were defined in the separate [package](https://github.com/kubakolecki/ros_common_messages). slam_deep mapper reads GeoreferencedStereoImage. This message has to be populated by SLAM workflow, for example visual or visual-inertial SLAM (TODO: provide example of ORB-SLAM3 and also rosbags). GeoreferencedStereoImage contains image and a sparse map from SLAM. slam_deep_mapper performs NDE and sends it to depth_map_optimizer using ImageBasedMappingData. depth_map_optimizer provides also a possibility to perform YOLO object detection but this feature is experimental for now. SLAM sparse map is also propagated via ImageBasedMappingData to depth_map_optimizer. depth_map_optimizer fuses depth map with SLAM sparse map and provides new optimized depth map.

## Datasets

## Evaluation
