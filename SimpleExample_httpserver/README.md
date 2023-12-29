# HTTP Server
You can host a very simple http server in python by simply running
```
python3 -m http.server
```
In web browser go to `http://localhost:8000/`. This is a simple file server with root directory being the one in which you ran above command.

## Docker cli
Now lets try to do this with docker. First we will pull a ubuntu 22.04 image. 
```
docker pull ubuntu:22.04
```
You should see the pulled image by running 
```
docker images
```
You can start an interactive session in the ubuntu image by
```
docker run -it ubuntu bash
```
This will also create a container with a unique name. Any changes that you make are containerized in this container. If you again run above command, it will create a new container. But if you want to use the container with the changes that you made, run following
```
docker start name_of_container
```
where the `name_of_container` can be obtained with `docker ps -a`. The option `-a` allows you to view stopped containers.

#### Python Http Server
First start an interactive session in docker, either create a new container or start existing. You can start and interactive session of existing container by
```
docker start -i name_of_container
```
Install python
```
apt update
apt install python
```
Start server 
```
root@containerid:/# python3 -m http.server
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
```
But you wont see anything on `http://0.0.0.0:8000/` on the host web browser. To resolve this ports must be forwarded. You can do this initially before creating the container
```
docker run -p 8000:8000 -it ubuntu
```
where `-p [host_port]:[container_port]` forwards the port.

Or if after you have already created a container of your liking, you first create a image out of the container as follows
```
docker commit name_of_container name_of_image
```
Now create a new container as follows
```
docker run -p 8000:8000 -it name_of_image
```

