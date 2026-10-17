```bash
nmcli device status
```

```bash
nmcli connection modify eth0 ipv4.addresses 192.168.1.100/24
```

```bash
nmcli connection modify eth0 ipv4.gatway 192.168.1.1
```

```bash
nmcli connection modify eth0 ipv4.dns "8.8.8.8 8.8.4.4"
```

```bash
nmcli connection modify eth0 ipv4.method manual
```

```bash
nmcli connection up eth0
```

```bash
ls /sys/class/net
```
