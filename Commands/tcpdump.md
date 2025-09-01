```bash
sudo tcpdump -n icmp
```
and then in other terminal call
```bash
ping -c 1 1.1
```

### with udp
```bash
sudo tcpdump -i wlp2s0 src 192.168.0.254 and dst 1.0.0.1 and udp
```
```bash
sudo tcpdump -v -i wlp2s0 src 192.168.0.254 and dst 1.0.0.1 and udp
```
### with icmp
```bash
sudo traceroute -I 1.1
```
```bash
sudo tcpdump -i wlp2s0 src 192.168.0.254 and dst 1.0.0.1 and icmp
```

