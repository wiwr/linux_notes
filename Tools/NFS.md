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
```

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

# Firewall
### TCP and UDP 
```
Port 2049 (nfs) 
Port 111 (rpcbind) 
Port 20048 (showmount) 
```
### /etc/sysconfig/nfs 
```
RQUOTAD_PORT=49001 
LOCKD_TCPPORT=49002 
LOCKD_UDPPORT=49003 
MOUNTD_PORT=49004 
STATD_PORT=49005 
STATD_OUTGOING_PORT=49006 
RDMA_PORT=49007
```
# Mount options
```text
noauto     – does not mount automatically; requires a manual `mount` command
hard       – default; waits indefinitely to recover the connection
soft       – terminates the process if the connection is lost
rsize      – read block size; can be increased from the default 1024 to 8192
wsize      – write block size; can be increased from the default 1024 to 8192
timeo=#    – time (in tenths of a second) before another transmission attempt
retrans=#  – number of times the NFS client retries a request (after timeout)
retry=#    – number of minutes to keep retrying a failed mount
bg         – after initial failure, all retries happen in the background
fg         – after initial failure, all retries happen in the foreground, blocking others
```
