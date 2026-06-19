# Network
```bash
nmtui
```

```text
Edit Connection
Set manually
```

# Update
```bash
sudo apt update | sudo apt upgrade
```
# SSH
update configuration file
	remove login with root
	 change password to key
## Key to SSH
```bash
ssh-keygen -t ed25519 -C "user@host"
```
```bash
ssh-copy-id user@192.168.1.200
```

# Routing
```bash
ip route
```

# Hostname
```bash
cat /etc/hostname
```
```bash
vim /etc/hostname
```
```bash
hostnamectl
```

# Hosts
```bash
vim /etc/hosts
```

# Timezone
```bash
timedatectl
```

```bash
timedatectl list-timezones
```

```bash
sudo timedatectl set-timezone Europe/Warsaw
```

# Filewall
Check if is active
Check open ports

# SELinux
```bash
sestatus
```

# Users
```bash
useradd user
```

```bash
usermod -aG wheel user
```

```bash
passwd user
```
