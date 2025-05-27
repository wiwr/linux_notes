# ip
[[Network]]

```
ip addr show
```
or 
```
ip a
```

```
ip addr show dev enp2s0
```

```
sudo ip link set enp2s0 down
```
```
sudo ip link set enp2s0 up
```

```
sudo ip addr add 192.168.0.123/24 enp2s0
```

```
sudo ip addr del 172.16.250.105/24 enp2s0
```
```
ip route show
```
```
sudo ip route add 172.16.252.0/24 via 172.16.250.1 dev enp2s0
```
```
sudo ip route del 172.16.252.0/24 via 172.16.250.1 dev enp2s0
```
```
ip -s link show enp2s0
```

and option with watch 

```
watch ip -s link show enp2s0
```

```bash
sudo ip link set enp1s0 down
```

```bash
sudo ip link set enp1s0 up
```