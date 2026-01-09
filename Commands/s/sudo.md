 run bash as root
 ```bash
sudo bash
 ```

```bash
sudo -s
```

```bash
sudo -l
```

```bash
which sudo
```

```bash
cat /etc/sudoers
```
```bash
cat /etc/sudoers.d/user
```
```bash
groups user
```

```bash
usermod -aG sudo user
```

```bash
sudo !!
```

```bash
sudo visudo
```

```text
user1 ALL=(ALL:ALL) ALL
user2 ALL=(ALL:ALL) /usr/bin/apt
user3 ALL=(ALL:ALL) /usr/bin/apt,/usr/bin/rm
user4 ALL=(ALL:ALL) NOPASSWD: /user/bin/apt
user5 ALL=(ALL:ALL) ALL,!/usr/bin/apt
```


