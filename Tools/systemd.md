# systemd volume mount
## check drives
```bash
lsblk
```
## preparation of disk
```bash
sudo fdisk /dev/vdb
```
```
n
follow defaults
p
w
```
```bash
lsblk
```
```bash
sudo mkfs.ext4 /dev/vdb1
```
```bash
sudo blkid /dev/vdb1
```
```bash
systemd-escape -p --sufix=mount "/mnt/disk_b"
```
```bash
sudo vim /etc/systemd/system/mnt-disk_b.mount
```
```
[unit]
Description=Mount storage volume

[Mount]
What=/dev/disk/by-uuid/<UUID>
Where=/mnt/disk_b
Type=ext4
Options=rw,noatime

[Install]
WantedBy=multi-user.target
```
```bash
sudo systemctl daemon-reload
```
```bash
systemctl status mnt-disk_b.mount
```
```bash
ls -l /mnt
```
```bash
df -h
```
```bash
sudo systemctl start mnt-disk_b.mount
```
```bash
sudo systemctl enabled mnt-disk_b.mount
```
```bash
sudo systemctl stop mnt-disk_b.mount
```
### network share
```bash
sudo apt install nfs-common
```
```bash
systemd-escape -p --suffix=mount /mnt/nfs_share
```
```bash
sudo vim /etc/systemd/system/mnt-nfs_share.mount
```
```
[unit]
Description=Mount NFS

[Mount]
What=192.168.100.100:/mnt/share
Where=/mnt/nfs_share
Type=nfs
Options=defaults
TimeoutSec=5

[Install]
WantedBy=multi-user.target
```
```bash
sudo systemctl daemon-reload
```
```bash
systemctl status mnt-nfs_share.mount
```
```bash
ls -l /mnt
```
```bash
df -h
```
```bash
sudo systemctl start mnt-nfs_share.mount
```
```bash
sudo systemctl enabled mnt-nfs_share.mount
```
```bash
sudo systemctl stop mnt-nfs_share.mount
```
## automount
```bash
systemd-escape -p --suffix=automount /mnt/nfs_share
```
```bash
sudo vim /etc/systemd/system/mnt-nfs_share.automount
```
```
[unit]
Description=NFS Automount

[Mount]
Where=/mnt/nfs_share
TimeoutSec=20

[Install]
WantedBy=multi-user.target
```
```bash
sudo systemctl daemon-reload
```
```bash
systemctl status mnt-nfs_share.automount
```
```bash
ls -l /mnt
```
```bash
df -h
```
```bash
sudo systemctl start mnt-nfs_share.automount
```
```bash
sudo systemctl enabled mnt-nfs_share.automount
```
```bash
sudo systemctl stop mnt-nfs_share.automount
```