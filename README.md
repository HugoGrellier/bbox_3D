# bbox_3D

## Authors

- Simon ERNST
- Thomas Curé

## Description

### Node coordinates_point_cloud

get_coordinate_object.py

Receives the BoudingBoxes message from darknet_ros, calculate its center and combine it with a 3D-point from a PointCloud.
Each data will be sent via a ROS message ( with the name, score, x, y, z coordinates) in the map frame.

### Node tf_broadcaster

tf_broadcast.py

Receives the message and will execute the saving mecanism as an Interest Point via the MapManager.
Other services are also provided such as the [division of the map in several rooms](https://github.com/Robocup-Lyontech/bbox_3D/blob/master/Documentation%20d%C3%A9coupage%20de%20la%20map%20en%20pi%C3%A8ces.pdf).

### Dependencies
If you are working on a PC with ROS Kinetic :
```bash
sudo apt-get install ros-kinetic-ros-numpy
sudo apt-get install ros-kinetic-rospy-message-converter
```
For every device :
```bash
sudo pip install shapely
```

Interest point of CPE Arena
From your catkin ws

```bash
mkdir -p data/world_mng/interest_points && mkmdir -p data/world_mng/temp
cd data/world_mng/interest_points
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1-1aMc3yNnchlErcB0kWB2Wnfu7LHoqSU' -O place_bedroom.coord
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=177ZgRUUwLq52WdOIyInkIsmHWUuHjjSS' -O place_diningRoom.coord
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1Nmtjj6c_4iCT9Izj-2C2aJWZ9oorFPTV' -O place_entrance_cleanup.coord
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1iKBGruOFCd2JY5DYf8-vIcSQXe48ywcK' -O place_entrance_recep.coord
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1QaogjPKw-Zo5hE7AA8WtjPNotdMheSwf' -O place_kitchen.coord
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1mKy7Q-iU-Q9EQu_WWW8XbWNhdjiWFMeZ' -O place_livingRoom.coord




## Usage : 
```bash
roslaunch coordinates_point_cloud tf_bbox.launch
```
This will launch the two previous nodes.
It will also launch a static transform publisher in order to have the correct orientation for the Kinect.

### Configuration

config file is located in coordinates_point_cloud/config/config.yaml
Important parameters are : 
- depth topic (topic where the PCL is published)
- tf_frame_source (the frame where the PCL is originating)

