```bash
cd /etc/netplan
```

```bash
ip a
```

```bash
ls
```

```bash
sudo vim 1-network-manager-all.yaml
```

```text
network:
  version:2
  renderer: NetworkManager
  ethernets:
    enp0s1: 
      dhcp4: no
      addresses: [192.168.1.111/24]
      gateway4: 192.168.1.1
      nameservers:
          addresses: [192.168.1.2,192.168.1.3]
```

```bash
sudo netplan try
```

```bash
sudo netplan apply
```

```bash
ip a
```