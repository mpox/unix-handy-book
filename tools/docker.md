# Docker

### Containers

List all running containers

	docker container ls                                

List all containers, even those not running

	docker container ls -a

Gracefully stop the specified container

	docker container stop <hash>           

Force shutdown of the specified container

	docker container kill <hash>         

Remove specified container from this machine

	docker container rm <hash>        

Remove all containers

	docker container rm $(docker container ls -a -q)         

Remove all exited containers

    docker rm $(docker ps -a -q -f status=exited)

Stats on memory/cpu usage of a particular containers

	docker stats              

Details about a container

	docker inspect <hash>                                

### Listing, removing images

List all images on this machine

	docker image ls -a                             

Remove specified image from this machine

	docker image rm <image id>            

Remove all images from this machine

	docker image rm $(docker image ls -a -q)   

### Building images from Dockerfile

Create image using Dockerfile of current directory

	docker build -t ubuntu-with-mc .
	docker build -t friendlyhello .  

### Running

Run command inside new container

	docker run -it busybox ls -l
	docker run -it alpine /bin/sh

Run container mapping port 4000 to 80

	docker run -p 4000:80 friendlyhello  

Same thing, but in detached mode

	docker run -d -p 4000:80 friendlyhello         

### Running parameters

When running docker-in-docker the volumes from host machine which are attached to guest can be accessed by docker in guest docker as follows

    --volumes-from=$HOSTNAME

Start container in specified working directory

    -w /home/app


### Volumes

Creating empty volumes

	docker volume create --name nexus-data

Start container with empty volume attached

	docker run -d -p 8081:8081 -v nexus-data:/nexus-data --name nexus sonatype/nexus3

Start container with host directory mounted as a container volume

	docker run -d -p 8081:8081 -v <host directory path>:/nexus-data --name nexus sonatype/nexus3

### Extracting container fs

Export contener `fs` to tar

	docker export c4b2743ea5bb > /Downloads/dockerexporttest.tar

Or to tar.gz

	docker export c4b2743ea5bb | gzip > /Downloads/dockerexporttest.tgz

Create container from archive

	cat /Downloads/dockerexporttest.tar | docker import - some-name-for-imported:latest

Or from tar.gz

	zcat /Downloads/dockerexporttest.tgz | docker import - c4b2743ea5bb


### Docker image registry

Log in this CLI session using your Docker credentials

	docker login             

Tag <image> for upload to registry

	docker tag <image> username/repository:tag  

Upload tagged image to registry

	docker push username/repository:tag            

Run image from a registry

	docker run username/repository:tag                  


### Docker machine

Create new docker machine

	docker-machine create --driver virtualbox myvm1
	docker-machine create --driver virtualbox myvm2

> Creates Virtualbox virtualmachine to be used as docker host

List available machines

	docker-machine ls

Get IP of default docker machine

    docker-machine ip default

Switch docker CLI to "default" VM

	eval $(docker-machine env default)           

Switch back to Docker Desktop

	eval $(docker-machine env -u)                    


### Creating Dockerfile

	mkdir docker_container
	cd docker_container
	touch Dockerfile

Example Dockerfile

```
FROM ubuntu
MAINTAINER Marek <mpoks@valuelogic.one>

RUN apt-get update && apt-get install -y mc
```

Build container

	docker build -t ubuntu-with-mc .


Another Dockerfile
```
# Use an official Python runtime as a parent image
FROM python:2.7-slim

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
ADD . /app

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```
Contents of `requirements.txt` used by above container

	Flask
	Redis

### Terms

- **docker-engine** - docker engine running containers
- **docker-machine** - virtual machine where docker-engine is running,
usually VirtualBox
- **docker-compose** - for composing multiple containers into 
one single services set (application). Whole configuration 
is in one single YAML file
- **Hyperkit** - native virtualization engine for Mac, it is used instead of VirtualBox (on Mac)
- **Docker Desktop** - uses Hyperkit as a host for 
docker-engine, by this docker can be run natively on Mac 
without using docker-machine
- **Docker Toolbox** - Deprecated

### Installation

On Mac you install **Docker Desktop**, which for hosting docker-engine uses Hyperkit instead of VirtualBox

