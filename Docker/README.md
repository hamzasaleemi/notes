# Docker Notes

## Container
Executable Package that bundles an application and its dependencies. It is runnable instance of Docker Image.

## Image
A Docker image is a read-only template containing instructions for creating a Docker container. It essentially serves as a blueprint or a snapshot of an application and its entire environment.

## Setup
* Install Docker
* Install WSL

## DockerHub
Same as github. It is used to create repositories for Docker Images.

## Commands
* `docker pull [Image Name]`: This command will get the docker image locally if not present from docker hub. Can be pull different version by adding version to image name like image:version
* `docker images`: This command will list all local images.
* `docker run -it [Image Name]`: This will run the image file and create a container and execute it.
    * `-it`: interactive parameter we will be able to access the container commandline.
    * `--name [Name]`: name of the new container
    * `-d`: run container in detached mode
    * `-p HOSTPORT:CONTAINERPORT`: Port mapping of host to container.
    * `--network [Network Name]`: Assign a docker network. 
* `docker ps -a`: List all containers.
* `docker start [Container Name or ID]`: Start the container.
* `docker stop [Container Name or ID]`: Stop the container.
* `docker rmi [Image Name or ID]`: Delete the docker image.
* `docker rm [Container Name or ID]`: Delete the docker container.
* `docker logs [Container Name or ID]`: Print logs of container.
* `docker exec -it [Container Name or ID] /bin/bash`: Execute command in container.

## Docker VS Virtual Machine
Docker only uses application layer but VM also uses OS Host Kernal Layer.

## Docker Network
A network for containers to interacte with each other.

## Commands
* `docker network ls`: List all networks
* `docker network create [Network Name]`: Create a new network.

## Docker Compose
A tool for defining and running multi-container applications. We write all docker commands in yaml(yet another markup language) file and then run it to handle multiple containers.

## Commands
* `docker compose -f [File Name].yaml up -d`: Run all docker commands and create images and containers and execute them.
* `docker compose -f [File Name].yaml down`: Delete all related images and containers.