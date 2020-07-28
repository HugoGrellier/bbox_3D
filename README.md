# bbox_3D

## Authors

Simon ERNST

## Description

### Node coordinates_point_cloud

get_coordinate_object.py

Receives the BoudingBoxes message from darknet_ros, calculate its center and combine it with a 3D-point from a PointCloud.
Each data will be sent via a ROS message ( with the name, score, x, y, z coordinates) in the map frame.

### Node tf_broadcaster

tf_broadcast.py

Receives the message and will execute the saving mecanism as an Interest Point via the MapManager.
Other services are also provided such as the [division of the map in several rooms](https://github.com/Robocup-Lyontech/bbox_3D/blob/master/Documentation%20d%C3%A9coupage%20de%20la%20map%20en%20pi%C3%A8ces.pdf).

## Usage : 
```bash
roslaunch coordinates_point_cloud tf_bbox.launch
```
This will launch the two previous nodes.


### Configuration

config file is located in coordinates_point_cloud/config/config.yaml
Important parameters are : 
- depth topic (topic where the PCL is published)
- tf_frame_source (the frame where the PCL is originating)

