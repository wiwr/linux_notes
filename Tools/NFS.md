# Server
```bash
sudo apt install nfs-kernel-server
```
```bash
sudo mkdir -p /exports/backup
```
  ```bash
sudo mv /etc/exports /etc/exports.org
```
```bash
sudo vim /etc/exports

Provide information follow 
```properties
/exports/backup 192.168.122.0/255.255.255.0(rw,no_subtree_check)
```
```bash
exportfs -ar
```
```bash
exportts -v
```
```bash
sudo systemctl restart nfs-kernel-server
```
```bash
sudo systemctl status nfs-kernel-server
```
```bash
ufw allow from 192.168.122.101 to any port nfs
```
# Client
```bash
sudo apt install nfs-common -y
```
```bash
showmount --exports 192.168.122.171
```
```bash
sudo mkdir /mnt/nfs/backup
```
```bash
sudo mount 192.168.122.171:/exports/backup /mnt/nfs/backup
```
```bash
showmount --exports 192.168.122.171
```
```bash
sudo umount /mnt/nfs/backup
```
```bash
sudo rmdir /mnt/nfs/backup/
```
# AutoFS
```bash
sudo apt install autofs -y
```
```bash
sudo vim /etc/auto.master
```
add in auto.master
```
/mnt/nfs /etc/auto.nfs --ghost --timeout=60
```
```bash
sudo vim /etc/auto.nfs
```
add in auto.nfs
```
backup -fstype=nfs4,rw 192.168.122.171:/exports/backup
```
```bash
sudo systemctl start autofs
```
```bash
sudo systemctl status autofs
```
```bash
sudo mount -a
```
```bash
ls /mnt/nfs
```

# Client with AutoFS
```bash
sudo apt install nfs-common autofs -y
```
```bash
showmount --exports 192.168.122.171
```
```Shell
sudo vim /etc/auto.master
```
add in auto.master
```
/mnt/nfs /etc/auto.nfs --ghost --timeout=60
```
```bash
sudo vim /etc/auto.nfs
```
add in auto.nfs
```
backup -fstype=nfs4,rw 192.168.122.171:/exports/backup
```
```bash
sudo systemctl start autofs
```
```bash
sudo systemctl status autofs
```
```bash
sudo mount -a
```
```bash
ls /mnt/nfs
```

# Additional information
```ini
Port 2049
```