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

```bash
sudo tcpdump -i wlp2s0 -v host 192.168.1.1
```
```bash
sudo tcpdump -i wlp2s0 -v dest 192.168.1.222
```
### trafic from all devices in network
```bash
sudo tcpdump -i wlp2s0 -v net 192.168.1.0/24
```
```bash
sudo tcpdump -i wlp2s0 -v net 192.168.1.0/24 and tcp
```

### with specific port
```bash
sudo tcpdump -i wlp2s0 -v src port 443 and dst 192.168.1.222
```

### save trafic
```bash
sudo tcpdump -w /tmp/traffic.pcap -i wlp2s0 -v 'tcp and net 192.168.1.0/24'
```
### good practice
put filter in quotation marks
```bash
sudo tcpdump -i wlp2s0 -v 'src port 443 and dst 192.168.1.222'
```