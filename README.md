<!--
 * @Description: 
 * @Author: jmx
 * @Date: 2023-06-23 15:00:04
 * @LastEditTime: 2023-06-28 23:09:46
 * @LastEditors: Please set LastEditors
-->
# MS-VRO

## Dataset

### Download Links

The dataset is uploaded [here](https://nas.orca-tech.cn:5000/sharing/BaLExn9xu). The rosbags are all compressed. To use the dataset, you can first download and decompress the rosbags.

### Details

（1）Data information

```python
/camera/color/image_raw        # D435i image, 1280 * 720, 30Hz
/camera/depth/image_rect_raw   # D435i depth image, 1280 * 720, 30Hz
/camera/imu                    # D435i IMU data
/imu/data                      # IMU data, 100Hz
/ouster/points                 # Ouster Lidar point cloud, 10Hz
/ouster/imu                    # Ouster IMU, 100Hz
/radar/points                  # Radar point cloud, 10Hz
```

 （2）Extrinsic and intrinsic parameters

```python
# Camera intrinsic parameters
FocalLength=[921.376281738281, 921.494750976562]
principalPoint = [624.489196777344, 368.375915527344];
imageSize = [1280, 720];
RadialDistortion = [0,0];
TangentialDistortion = [0,0];


# IMU-Camera (IMU inside the camera) extrinsic parameters
# Transformation from IMU to camera
T = [0.999976,0.000693444,0.00683458, 0.0201056953519583,
     -0.000695267,1.0  , 0.000264293, -0.00504042906686664,
     -0.0068344,-0.000269039, 0.999977,  -0.0114226331934333,
     0.0,0.0,0.0,1.0]

# Lidar-Camera extrinsic parameters
t = [0.250620404253477, -0.036564016917019, -0.112904341600731]
R = [0.004811388191894, -1.003550418032114, -0.003116251098663;
     0.009193652813973, -0.003796995446461, -0.991628647673876;
     1.004854476258477,  0.009184319190004,  0.016948508611267]
PointsInCamera = R * (PointsInLidar - t');

# Radar-Lidar extrinsic parameters
t = [0.073, -0.0103, 0.137];
R = [-0.013746383632443,  0.999905514004713,  0;
     -0.999905514004713, -0.013746383632443,  0;
      0                ,  0 ,                 1.00];
PointsInLidar = R * PointsInRadar + t';

# Radar-Camera extrinsic parameters
t = [-0.027990630551015, -0.249545008991387, -0.174005935288756];
R = [1.003389457384155, 0.018606122623860, -0.003116251098663;
     0.003670257205003, 0.009244979098594, -0.991628647673876;
    -0.022996566525891, 1.004633280408180,  0.016948508611267];
PointsInCamera = R * PointsInRadar + t';

# Radar-IMU(independent IMU) extrinsic parameters
R = [0, -1, 0;
     1,  0, 0;
     0,  0, 1]
t = [-0.032, 0.038, 0.084]



```



## Code

Under preparation....






