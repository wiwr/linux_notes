# LVM Terminology

| Abbreviation | Full Name                  |
| ------------ | -------------------------- |
| PV           | Physical Volume            |
| VG           | Volume Group/Virtual Group |
| LV           | Logical Volume             |
```bash
$ lsblk
```

```bash
$ sudo pvs
```

```bash
$ sudo vgs
```

```bash
$ sudo lvs
```

```bash
$ sudo pvcreate /dev/sdb
```

```bash
$ sudo pvdisplay
```

```bash
$ sudo vgcreate blue_vg /dev/sdb /dev/sdc1 /dev/sdd
```

```bash
$ sudo vgdisplay
```

```bash
$ sudo lvcreate –l 100%FREE data_vg –n data_lv
```

```bash
$ sudo lvcreate –L 500M data_vg –n data_lv
```

```bash
$ sudo lvdisplay
```

```bash
$ sudo lvdisplay -m
```

```bash
$ sudo mkfs.ext4 /dev/data_vg/data_lv
```

```bash
$ sudo mkdir /data
```

```bash
$ sudo ls / -lh
```

```bash
$ sudo mount /dev/data_vg/data_lv /data
```

```bash
$ df –h
```

```bash
$ sudo umount /dev/data_vg/data_lv
```

```bash
$ df –h
```

```bash
$ sudo lvremove data_vg/data_lv
```

```bash
$ sudo vgremove data_vg
```

```bash
$ sudo pvremove /dev/vdb /dev/vdc /dev/vdd /dev/vde /dev/vdf
```

```bash
$ sudo pvdisplay
```

```bash
$ lsblk
```

```bash
$ sudo vgextend data_vg /dev/vdg
```

```bash
$ sudo lvextend –L +5G /dev/data_vg/data_lv
```

```bash
$ df –h
```

```bash
$ lsblk –f
```

```bash
$ sudo resize2fs /dev/data_vg/data_lv
```

```bash
$ df- h
```

```bash
$ sudo lvdisplay –m
```

```bash
$ sudo lvextend –l +100$FREE /dev/data_vg/data_lv
```

```bash
$ sudo lvs
```

```bash
$ df –h
```

```bash
$ sudo vgextend data_vg /dev/vdh
```

```bash
$ sudo lvextend –L +500M /dev/data_vg/data_lv -r
```

```bash
$ sudo lvs
```

```bash
$ sudo lvremove data_vg/data_lv
```

```bash
$ sudo pvs
```

```bash
$ sudo lvcreate –L 4500M –n lv_mirror data_vg /dev/vdb
```

```bash
$ sudo lvdisplay –m
```

```bash
$ sudo lvconvert –m1 data_vg/lv_mirror /dev/vdd
```

```bash
$ sudo lvs
```

```bash
$ sudo lvdisplay –m
```

```bash
$ lsblk
```

```bash
$ sudo lvconvert –m0 data_vg/lv_mirror /dev/sdb
```

```bash
$ sudo lvremove data_vg/lv_mirror
```

```bash
$ sudo lvcreate –l 100%FREE data_vg –n moveme /dev/vdb
```

```bash
$ lsblk
```

```bash
$ sudo lvconvert –m1 data_vg/moveme /dev/vdd
```

```bash
$ sudo lvconvert –m1 –type mirror –corelog data_vg/movemve /dev/vdd
```

```bash
$ lsblk
```

```bash
$ sudo lvdisplay –m
```

```bash
$ sudo lvconvert –m0 data_vg/moveme /dev/vdb
```

```bash
$ sudo lvdisplay –m
```

```bash
$ sudo lvconvert –m1 –type mirror –mirrorlog disk data_vg/moveme
```

```bash
$ lsblk
```

```bash
$ sudo lvs
```

```bash
$ sudo lvremove data_vg/moveme
```

```bash
$ sudo lvcreate --type raid0 –L 600M –n lv_raid0 –i 2 data_vg
```

```bash
$ sudo lvs
```

```bash
$ sudo lvdisplay –m
```

```bash
$ sudo lvremove data_vg/lv_raid0
```

```bash
$ sudo lvcreate --type raid0 –l 100%FREE –n lv_raid0 –i 2 data_vg /dev/vdb /dev/vdd
```

```bash
$ sudo lvs
```

```bash
$ sudo pvs
```

```bash
$ sudo lvcreate –-type raid5 –n lv_raid5 –L 2040 –i 2 data_vg
```

```bash
$ sudo lvdisplay -m
```

```bash
$ lsblk
```

```bash
$ sudo mkfs.ext4 /dev/data_vg/lv_raid5
```

```bash
$ sudo mount /dev/data_vg/lv_raid5 /mnt/raid5
```

```bash
$ sudo dd if=/dev/urandom of=newfile1 bs=1M count=300
```

```bash
$ sudo dd if=/dev/urandom of=newfile2 bs=1M count=200
```

```bash
$ sudo lvdisplay -m
```

```bash
$ sudo pvs
```

```bash
$ sudo vgextend data_vg /dev/vdh
```

```bash
$ sudo lvconvert –repair data_vg/lv_raid5
```

```bash
$ sudo vgreduce --removemissing data_vg
```

```bash
$ sudo lvs
```

```bash
$ sudo pvs
```

```bash
$ sudo lvcreate –L 500M data_vg –n linear_lv
```

```bash
$ sudo mkfs.ext4 /dev/data_vg/linear_lv
```

```bash
$ sudo mkdir /mnt/lvm1
```

```bash
$ sudo mount /dev/data_vg/linear_lv /mnt/lvm1
```

```bash
$ cd /mnt/lvm1
```

```bash
$ sudo lvcreate –L 50M –s /dev/data_vg/linear_lv –n snap1
```

```bash
$ sudo lvcreate –L 600M –s /dev/data_vg/linear_lv –n snap2
```

```bash
$ sudo lvs
```

```bash
$ sudo lvdisplay
```

```bash
$ sudo dd if=/dev/urandom of=testFile1 bs=1M count=100
```

```bash
$ sudo lvs
```

```bash
$ sudo dd if=/dev/urandom of=testFile3 bs=1M count=150
```

```bash
$ sudo lvremove data_vg/snap1
```

```bash
$ sudo mkdir /mnt/lvm2
```

```bash
$ sudo mount /dev/data_vg/snap2 /mnt/lvm2
```

```bash
$ ls –lh /mnt/lvm2
```

```bash
$ sudo umount /mnt/lvm[23]
```

```bash
$ sudo umount /mnt/lvm1
```

```bash
$ sudo lvconvert –merge /dev/data_vg/snap3
```

```bash
$ sudo lvs
```

```bash
$ sudo umount /mnt/lvm1
```

```bash
$ sudo lvchange --activate n data_vg/linear_lv
```

```bash
$ sudo lvchange --activate y data_vg/linear_lv
```