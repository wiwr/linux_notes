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