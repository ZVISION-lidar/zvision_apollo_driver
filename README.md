# 1 Introduction

Apollo driver for zvision lidar.

# 2 Prerequisites
 Apollo version  required [Apollo V5.5.0](https://github.com/ApolloAuto/apollo/releases/tag/v5.5.0)

# 3 Components
1. [Driver](https://github.com/ZVISION-lidar/zvision_apollo_driver/tree/master/apollo/modules/drivers/zvision/driver): Driver receives UDP data packets from lidar sensor, and packages the data packets into a frame of scanning data in the format of ZvisionScan. ZvisionScan is defined in file below:
	```
    modules/drivers/zvision/proto/zvision.proto
	```
2. [Parser](https://github.com/ZVISION-lidar/zvision_apollo_driver/tree/master/apollo/modules/drivers/zvision/parser): Parser takes one frame data in format of ZvisionScan as input, converts the cloud points in the frame from spherical coordinate system to Cartesian coordinates system, then sends out the point cloud as output. The pointcloud format is defined in file below:
	```
    modules/drivers/proto/pointcloud.proto
	```
3. [Compensator](https://github.com/ZVISION-lidar/zvision_apollo_driver/tree/master/apollo/modules/drivers/zvision/compensator): Compensator takes pointcloud data and pose data as inputs. Based on the corresponding pose information for each cloud point, it converts each cloud point information aligned with the latest time in the current lidar scan frame, minimizing the motion error due the movement of the vehicle. Thus, each cloud point needs carry its own timestamp information.

Notes: Compensator is not test yet, and will update soon.

# 4 Build
```
	cd /apollo
    bash apollo_build_zvision build_zvision
 ```
   
# 5 Sample
You can run a sample dag file in the modules/drivers/zvision/dag directory. For reference, directory named [offline_calibration](https://github.com/ZVISION-lidar/zvision_apollo_driver/tree/master/apollo/modules/drivers/zvision/dag/offline_calibration) provides the samples which you can specify a local calibration file for the pointcloud, so [online_calibration](https://github.com/ZVISION-lidar/zvision_apollo_driver/tree/master/apollo/modules/drivers/zvision/dag/online_calibration) is.
1. Run zvision ML30 lidar with offline calibration.
   ```
    mainboard -d /apollo/modules/drivers/zvision/dag/offline_calibration/zvision_ml30.dag
    ```
2. Run zvision ML30SA1 lidar with online calibration.
    ```
    mainboard -d /apollo/modules/drivers/zvision/dag/online_calibration/zvision_ml30sa1.dag
    ```