# Install
```bash
sudo apt install iperf3 -y
```

```bash
command -v iperf3
```
# Usage
### set server
```bash
iperf3 -s
```
### set customer
ip points server ip address
```bash
iperf3 -c 192.168.1.222
```

to set interface 
```bash
iperf3 -c 192.168.1.222 -B 192.168.1.100
```
reverse mode
```bash
iperf3 -c 192.168.1.222 -R
```