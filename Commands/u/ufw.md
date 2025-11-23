```bash
sudo apt install ufw
```
```bash
sudo ufw disable 
```
```bash
sudo ufw enable
```
```bash
sudo ufw status 
```
```bash
sudo ufw status verbose 
```
```bash
sudo ufw allow from 8.8.8.8 proto tcp to any port 22 
```
```bash
sudo ufw status numbered 
```
```bash
sudo ufw allow in on enp0s3 from 8.8.8.8 
```
```bash
sudo ufw allow ssh
```
```bash
sudo ufw default deny incoming 
```
```bash
sudo ufw default deny outgoing 
```
```bash
sudo ufw default allow outgoing 
```
```bash
sudo ufw default allow incoming 
```