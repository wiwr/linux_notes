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
