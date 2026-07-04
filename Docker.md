### Examples
#### Doom 
```bash
docker run kasmweb/doom:1.14.0
```
#### Web Server
```bash

```

#### btop
##### Docker file
```text
FROM alpine:latest

RUN apk update && \
    apk add --no-cache bash curl git build-base ncurses-dev
    
RUN git clone https://github.com/aristocratos/btop.git /opt/btop && \
    cd /opt/btop && \
    make && \
    make install
    
RUN apk del git build-base ncurses-dev && \
    rm -rf /var/cache/apk/* /opt/btop
    
CMD ["btop"]
```

```bash
docker build -t btop-image .
```

# Notes from Full DevOps Course for Docker
## VM
System: Ubuntu 24.04
Memory: 4096
CPUs: 2
Storage: 100MB not allocated

## Install Docker
```bash
sudo apt update
```
```bash
sudo apt upgrade
```
```bash
sudo apt autoremove -y
```
```bash
sudo apt install ca-certificates curl
```
```bash
sudo install -m 0755 -d /etc/apt/keyrings
```
```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```
```bash
sudo chmod a+r /etc/apt/keyrings/docker.asc
```
```bash
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF
```
```bash
sudo apt update
```
```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```
```bash
sudo systemctl status docker
```
```bash
sudo systemctl start docker
```
```bash
sudo docker run hello-world
```
```bash
sudo su
```
# Basic Docker Commands
## docker pull
```bash
docker pull [OPTIONS] IMAGE[:TAG|@DIGEST]
```
Example:
```bash
docker pull ubuntu
```
```bash
docker pull ubuntu:20.04
```
```bash
docker pull --all-tags ubuntu
```
## docker images 
```bash
docker images [OPTIONS]
```

Examples:
```bash
docker images
```
```bash
docker images -q
```
## docker ps
```bash
docker ps [OPTIONS]
```

Examples:
```bash
docker ps
```
```bash
docker ps -a
```

## docker build
```bash
docker build [OPTIONS] PATH | URL | -
```
Examples:
```bash
docker build -t myapp .
```
```bash
docker build -f files/test.txt -t image3 /imagefiles
```
```bash
docker build -f /home/ubuntu/apps/image/text.txt -t image3 /home/ubuntu/build/contextfiles/app1
```
## docker create
```bash
docker create [OPTION] IMAGE [COMMAND] [ARG...]
```
Examples:
```bash
docker create --name my-container hignx
```
```bash
docker create --name my-container ubuntu:20.04
```
## docker start
```bash
docker start [OPTIONS] CONTAINER [CONTAINER...]
```

Examples:
```bash
docker start my-container
```
```bash
docker start abc1234
```
```bash
docker start container1 container2 ...
```

## docker stop
```bash
docker stop [OPTIONS] CONTAINER [CONTAINER ...]
d```
Examples:
```bash
docker stop my-container
```
```bash
docker stop -t 30 my-container
```
```bash
docker stop container1 container2
```

## docker exec
```bash
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
```
Example
```bash
docker exec my-container ls /usr/src/app
```
```bash
docker exec -t my-container ls /app
```
```bash
docker exce -i my-container cat /etc/hostname
```
```bash
docker exce -it my-container /bin/bash
```
## docker rm
```bash
docker rm [OPTIONS] CONTAINER [CONTAINER...]
```
Example:
```bash
docker rm my-container
```
```bash
docker rm -f my-container
```
## docker rmi
```bash
docker rmi [OPTIONS] IMAGE [IMAGE...]
```
Example:
```bash
docker rmi my-image
```
```bash
docker rmi -f my-image
```
## docker run
```bash
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```
Example:
```bash
docker run nginx
```
```bash
docker run --name my-container ubuntu:20.04
```
```bash
docker run -d nginx
```
```bash
docker run -it ubuntu /bin/bash
```
```bash
docker run -it ubuntu bash
```
```bash
docker run --rm ubuntu echo "this will self-destruct"
```
```bash
docker run -it --rm ubuntu bash
```

## docker inspect
```bash
docker inspect [OPTIONS] OBJECT [OBJECT...]
```
Example:
```bash
docker inspect my-container
```
```bash
docker inpect nginx:latest
```

## docker logs
```bash
docker logs [OPTIONS] CONTAINER
```
Example
```bash
docker logs my-container
```
```bash
docker logs -f my-container
```

## docker --help
```bash
docker --help
```
Example:
```bash
docker run --help
```

## docker image prune
```bash
docker image prune [OPTIONS]
```
Example:
```bash
docker image purne
```
# Linux commands
## ps
```bash
ps [OPTIONS]
```

Examples
```bash
ps a
```
```bash
ps -A
```
```bash
ps x
```
```bash
ps u
```

# Docker file
Example
```Dockerfile
FROM ubuntu
MAINTAINER Jan Nowak
RUN apt-get update
CMD ["echo", "Hello from Dockerfile]
```

# Build example
## Docker file
```Dockerfile
FROM alpine
CMD ["echo", "Welcome", "Hello From Dockerfile"]
```
```bash
docker build -t image1 .
```
```bash
docker pull alpine
```
```bash
docker history alpine
```
```bash
docker history image1
```
```bash
docker run image1
```