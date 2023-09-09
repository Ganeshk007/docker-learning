# docker-learning
Basics of docker



## Flow
Dockerfile => build as => Image => run as => Containers



## To search docker images in terminal
```
docker search ubuntu22.04

or

hub.docker.com
```

## Image Commands:
docker image ls -> To list all images

docker rmi image-name -> To remove image by name

docker pull image-name -> To pull image from docker hub

docker run image-name -> To run image by name (it creates a container and run)

docker run -it image-name -> To run image by name with interactive terminal (it creates a container and run)

docker tag image-id newname:v1 -> To set tag name for image

## Container Commands:

docker ps -> To list all running containers

docker ps -a -> To list all containers

docker start container-name/container-id -> To start stoped container

docker exec -it container-id sh -> To execute command in started container

docker stop container-id -> To stop container

docker restart container-id -> To restart container
