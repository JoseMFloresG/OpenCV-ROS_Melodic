# OpenCV-ROS_Melodic
#### ROS Melodic program to calibrate a camera

## Requisitos
#### ROS Melodic

## Instalar OpenCV
```
sudo apt update
sudo apt install python3-opencv
sudo apt install build-essential cmake git pkg-config libgtk-3-dev \
    libavcodec-dev libavformat-dev libswscale-dev libv4l-dev \
    libxvidcore-dev libx264-dev libjpeg-dev libpng-dev libtiff-dev \
    gfortran openexr libatlas-base-dev python3-dev python3-numpy \
    libtbb2 libtbb-dev libdc1394-22-dev
```
Referencias: [OpenCV Installation](https://linuxize.com/post/how-to-install-opencv-on-ubuntu-18-04/)

## Clonar paquete para la calibracion
```
cd ws/src
git clone https://github.com/ros-perception/image_pipeline.git
cd image_pipeline
git checkout melodic
```
Referencias: [camera_calibration](http://wiki.ros.org/camera_calibration#cameracalibrator.py)

## Crear paquete (O descargalo de aqui)
```
cd ws/src
catin_create_pkg vision rospy cv_bridge sensor_msgs
```
#### Copia el imshow.launch y el image_publisher.py 
```
cd /ws
catkin_make
```
Referencias: [Video Publish Explanation](https://www.youtube.com/watch?v=2l913YwWYe4&t=24s)

## Pruebas finales
#### Para ver que si este publicando el video
```
roslaunch vision imshow.launch
rotopic echo /webcam
```
#### Para hacer la calibracion de la camara
```
roslaunch vision imshow.launch
rosrun camera_calibration cameracalibrator.py --size 9x6 --square 0.0246 --no-service-check image:=/webcam camera:=/webcam
```


