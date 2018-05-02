![Screenshot](/capture.bmp)
Sample map built from [nsh_indoor_outdoor.bag](http://www.frc.ri.cmu.edu/~jizhang03/Datasets/nsh_indoor_outdoor.bag) (opened with [ccViewer](http://www.danielgm.net/cc/))

:white_check_mark: Tested with ROS Indigo and Velodyne VLP16. [(Screencast)](https://youtu.be/o1cLXY-Es54)

All sources were taken from [ROS documentation](http://docs.ros.org/indigo/api/loam_velodyne/html/files.html)

Ask questions [here](https://github.com/laboshinl/loam_velodyne/issues/3).

How to build with catkin:

```
$ cd ~/catkin_ws/src/
$ git clone https://github.com/laboshinl/loam_velodyne.git
$ cd ~/catkin_ws
$ catkin_make -DCMAKE_BUILD_TYPE=Release 
$ source ~/catkin_ws/devel/setup.bash
```
/**Modified by Chuanzhe Suo**/
1. Added the support to RS_lidar_32(Robosense Tech)(You can support RS_16 also just need change one line)
2. Modified the roslaunch file to launch

Running:

For RS-Lidar-32
$ roslaunch loam_velodyne loam_velodyne.launch

$ roslaunch rslidar_pointcloud rs_lidar_32.launch

(or other launch file read from pcap file. The pointcloud topic is "/rslidar_points")

For Velodyne

You need modify the launch file to change remap.
    <!-- remap from="/multi_scan_points" to="/velodyne_points" -->
    <remap from="/multi_scan_points" to="/rslidar_points" />
change the topic you used.
and run

$ roslaunch loam_velodyne loam_velodyne.launch lidartype:=HDL-32 (options: VLP-16  HDL-32  HDL-64E RS-32)

Then play the bag or launch the velodyne lidar you used.

/**Original Author**/

Running:
```
roslaunch loam_velodyne loam_velodyne.launch
```

In second terminal play sample velodyne data from [VLP16 rosbag](https://db.tt/t2r39mjZ):
```
rosbag play ~/Downloads/velodyne.bag 
```

Or read from velodyne [VLP16 sample pcap](https://midas3.kitware.com/midas/folder/12979):
```
roslaunch velodyne_pointcloud VLP16_points.launch pcap:="/home/laboshinl/Downloads/velodyne.pcap"
```



---
[Quantifying Aerial LiDAR Accuracy of LOAM for Civil Engineering Applications.](https://ceen.et.byu.edu/sites/default/files/snrprojects/wolfe_derek.pdf) Derek Anthony Wolfe

[ROS & Loam_velodyne](https://ishiguro440.wordpress.com/2016/04/05/%E5%82%99%E5%BF%98%E9%8C%B2%E3%80%80ros-loam_velodyne/) 
