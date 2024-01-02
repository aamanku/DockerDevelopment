FROM osrf/ros:noetic-desktop-full

RUN apt-get update 
RUN apt-get install build-essential git cmake pkg-config -y
RUN apt-get install -y libglpk-dev
RUN apt-get install -y python3-catkin-pkg 
RUN apt-get install -y ros-noetic-pybind11-catkin python3-catkin-tools ros-noetic-rqt-multiplot
RUN apt-get install -y libeigen3-dev libboost-all-dev 

RUN mkdir -p /home/Documents
WORKDIR /home

