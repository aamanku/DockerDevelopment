# OCS2 Docker environment
Following the steps in the [link](https://leggedrobotics.github.io/ocs2/installation.html).

Docker file
```
FROM ros:noetic

RUN apt update 
RUN apt install -y libglpk-dev
RUN apt install -y catkin ros-noetic-pybind11-catkin python3-catkin-tools ros-noetic-rqt-multiplot
RUN apt install -y libeigen3-dev libboost-all-dev 

RUN mkdir -p /home/Documents
WORKDIR /home
```
Build the image by
```
docker build -t "ocs2_docker:latest" .
```


To allow the docker to use the host's X11 socket run following command. Caution! This is the least secure way, since anyone can use the socket now. 
```
xhost +
```
Then run the image
```
docker run -it --net=host \
--env="DISPLAY" \
--env="QT_X11_NO_MITSHM=1" \
--volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
--volume="/home/${USER}/Documents:/home/Documents:rw" \
--name=dont_cry \
ocs2_docker:latest \
bash
```

