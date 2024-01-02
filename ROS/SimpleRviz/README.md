# ROS
Create a docker file with ros noetic. You can find existing ros images at the [Docker hub](https://hub.docker.com/_/ros). Here we will try to create a example of Dockerfile where you can run rviz in the container and vizualize it. First build an image with the Dockerfile
```
FROM ros:noetic

RUN apt update 
RUN apt install -y ros-noetic-rviz

# Mount point for the host
RUN mkdir -p /home/Documents 

# Set the working directory
WORKDIR /home 
```

Build the image by
```
docker build -t "rviz_ros:latest" .
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
rviz_ros:latest \
bash
```

To test the rviz gui first start the ros master 
```
roscore &
```
and then the rviz
```
rosrun rviz rviz
```
You should see rviz on the host.