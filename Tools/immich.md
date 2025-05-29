# Steps:
## Install Ubuntu LTS on proxmox as VM
## System post installation
```bash
sudo apt update && sudo apt upgrade -y
```

## Docker installation
```bash
sudo apt install -y docker.io
```
```bash
sudo systemctl enable --now docker
```
```bash
sudo apt install -y docker-compose
```

## immich installation
```bash
mkdir ./immich-app
```
```bash
cd ./immich-app
```
```bash
wget -O docker-compose.yml https://github.com/immich-app/immich/releases/latest/download/docker-compose.yml
```
```bash
wget -O .env https://github.com/immich-app/immich/releases/latest/download/example.env
```
```bash
sudo usermod -aG docker $USER
```
```bash
newgrp docker
```

## Update .env file

## Start the containers
```bash
docker compose up -d
```

## Connect to immich
```bash
http://<immich-server-ip>:2283
```

## Debug
```bash
docker compose version
```
```bash
docker --version
```
```bash
docker info
```