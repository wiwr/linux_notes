# Update
```bash
sudo apt update && sudo apt upgrade -y
```
```bash
sudo apt autoremove
```
```bash
sudo apt clean
```
# Automate updates
```
sudo apt install unattended-upgrades
```
add missing part
# root login
```bash
sudo passwd -l root
```
```bash
sudo usermod -aG sudo user_name
```
# Firewall
```bash
sudo ufw status
```
```bash
sudo ufw allow ssh
```
```bash
sudo ufw default deny incomming
```
```bash
sudo ufw enable
```
# SSH
## create key
```bash
ssh-keygen
```
## copy key
```bash
ssh-copy-id user@192.168.1.111
```
## update configuration on server
```bash
sudo vim /etc/ssh/sshd_config
```
```txt
PasswordAuthenticaton no
PermitRootLogin no
```
## restart ssh
```bash
sudo systemctl restart ssh
```
# Services
```bash
sudo systemctl list-unit-files --type=service | grep enabled
```
# secure files
```bash
sudo chmod 600 /etc/shadow
```
```bash
sudo chmod 600 /etc/gshadow
```
```bash
sudo chmod 644 /etc/passwd
```
```bash
sudo chmod 644 /etc/group
```
# audit
```bash
sudo apt install lynis
```
```bash
sudo lynis audit system
```
