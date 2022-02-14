## Docker Commands

### Images

| Command                                                                                        |               Action                                          |
|------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
|`docker build -t <image name>:<tag> .`                                                          | build docker container from Dockerfile                        |
|`docker images`  or `docker image list`                                                         | shows the list of container images on a machine               |
|`docker rmi <image id>`                                                                         | remove image                                                  |
|`docker image prune`                                                                            | remove images                                                 |
|`docker rmi $(docker images -q)`                                                                | delete all images (works only in Ubuntu terminal)             |
|`docker tag <source image name>:<tag> <target image name>:<tag>`                                | push docker image to Docker Hub                               |
|`docker push <image name>:<tag>`                                                                | push docker image to Docker Hub                               |

### Containers

| Command                                                                                        |               Action                                          |
|------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
|`docker run -p [external port]:[internal port] <image name>:<tag>`                              | create and start docker container from image                  |
|`docker run -p [external port]:[internal port] --name my-container <image name>:<tag>`           | create and start docker container from image                  |
|`docker create <image name>:<tag>`                                                              | create docker container without starting it                   |
|`docker run <image name>:<tag>` -p [external port]:[internal port]                              | create and start docker container from image                  |
|`docker run -p [external port]:[internal port] --name my-container <image name>:<tag>`          | create and start docker container from image                  |
|`docker run -it --rm <image name>:<tag>`                                                        | create/start container, remove after stop (CTRL+C)            |
|`docker run -it --rm -p 3000:80 --name mymicroservicecontainer mymicroservice`                  | create/start container, remove after stop (CTRL+C)            |
|`docker start <docker id>`                                                                      | start docker container                                        |
|`docker ps`                                                                                     | display all running containers                                |
|`docker ps -a`                                                                                  | display all containers with their status                      |
|`docker build -t <image name>:<tag> .`                                                          | build docker container from Dockerfile                        |
|`docker run -t <image name>:<tag> -f .\CreateTestDb.Dockerfile .`                               | build docker container from specified Dockerfile              |
|`docker exec -it <container-id> /bin/sh`    => `ls`                                             | Open a command in running container and display content       |

If you get error message `image operating system "windows" cannot be used on this platform` you need to switch to
Windows Containers on Docker -> Right Click on Docker Icon in Notification Area and choose `Switch to Windows Containers...`

| Command                                                                                        |               Action                                          |
|------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
|`docker exec <container name> ipconfig`                                                         | get the IP address of a running container                     |
|`docker exec -it <container id> bash`                                                           | interactive way to use terminal inside a container            |
|`docker attach --sig-proxy=false <container-id>`                                                | peek at container output stream --sig-proxy=false parameter   |
|                                                                                                | ensures CTRL+C will not stop process in container             |
|`docker ps -a`                                                                                  | list of running containers (-a slso show exited containers)   |
|`docker network`                                                                                | manage networking with Docker                                 |
|`docker pull microsoft/windowsservercore`                                                       | pull latest windowsservercore image from Docker Hub           |
|`docker rm <container-id>`                                                                      | remove a specific container                                   |
|`docker rm -f <container-id>`                                                                   | remove a specific running container                           |
|`docker rm $(docker ps -a -q)`                                                                  | delete all containers                                         |
|`docker system prune`                                                                           | clean up any resources — images, containers, volumes and      |
|                                                                                                | network sthat are dangling (not associated with a container)  |
|`docker system prune -a`                                                                        | to additionally remove any stopped containers and all unused  |
|                                                                                                | images (not just dangling images)                             |
|`docker stop $(docker ps -q)`                                                                   | stop all running containers  (in Git Bash command window)     |

### Docker Compose

| Command                                                                                        |               Action                                          |
|------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
|`docker-compose build`                                                                          | build containers, volumes,.. specified in docker-compose.yaml |
|`docker-compose up -d`                                                                          | spin up containers, volumes specified in docker-compos.yaml   |
|`docker-compose up --build -d`                                                                  | build + spin up containers,... specified in docker-compos.yaml|
|`docker-compose down`                                                                           | tear down docker-compose session                              |
|`docker-compose ps`                                                                             | overview of containers docker-compose session                 |
|`docker exec <container name>_1 env`                                                            | show environment variables from inside a container            |

ATTENTION: You may get error like: Error response from daemon: conflict: unable to remove repository reference IMAGE NAME  (must force) -
container 302e8bd is using its referenced image 3334b287844 -> a stopped container isn't actually removed.

### Docker Hub

| Command                                                                                        |               Action                                          |
|------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
|`docker login`                                                                                  | login to Docker Hub                                           |
|`docker tag <image-name> <your-docker-username>/<image-name></image-name>`                      | Rename/retag image for use in Docker Hub                      |
|`docker push <your-docker-username>/<image-name></image-name>`                                  | Push/upload the image to Docker Hub                           |

### Docker Parameters

| Parameter                                                                                      |               Description                                     |
|------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
|`-d`                                                                                            | detached, when you need to run a background service.          |
|`-p` 8080:80                                                                                    | expose inside container port 80 to port 8080 on your machine  |
|`--rm`                                                                                          | removes the container from list after container has stopped   |
|`-t`                                                                                            | tag                                                           |
|`-v`                                                                                            | volume                                                        |

### Volumes

| Command                                                                                        |               Action                                          |
|------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
|`docker volume create <volume name>`                                                            | create volume                                                 |
|`docker volume ls`                                                                              | overview volumes                                              |
|`docker volume prune`                                                                           | delete all volumes that are not in use                        |
|`docker volume rm <volume name>`                                                                | delete a volume by name                                       |
|`docker inspect <volume name>`                                                                  | inspect a volume                                              |
|`docker run -d -p 8083:3000 --name <container name> -v /d:/app:/<volume name> <image name>`     | Create and run container with volume path d:/app              |

### Howto resize Docker Virtual Hard disk

| Command                                                                                                   |               Action                               |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------|
|`docker image prune`                                                                                       | remove all dangling images                         |
| [powershell] `Optimize-VHD -Path "C:\ProgramData\DockerDesktop\vm-data\DockerDesktop.vhdx" -Mode Quick`   | optimize hard disk                                 |
