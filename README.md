# DockerDevelopment
 
## Installation
Install docker in ubuntu form this [link](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository).

Check if docker is installed properly by running
```
sudo docker run hello-world
```
To use docker without `sudo` follow the steps in this [link](https://docs.docker.com/engine/install/linux-postinstall/). TLDR run following
```
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
```
#### Docker Images and Containers
A Docker container is a self-contained, runnable software application or service. On the other hand, a Docker image is the template loaded onto the container to run it, like a set of instructions. For more information go to this [link](https://aws.amazon.com/compare/the-difference-between-docker-images-and-containers/).

To get a list of docker images run
```
docker images
```
To get a list of docker containers run
```
docker ps
```
## Developement with Docker
Following this [link](https://docs.docker.com/develop/).


