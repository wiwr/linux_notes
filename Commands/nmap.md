# Installation
```
sudo apt install nmap
```
# Scans
## specific ports
for single
```bash
nmap -p22 192.168.1.1
```
for multiple ports
```bash
nmap -p22-25 192.168.1.1
```
## detect specific service
```bash
nmap -p22-25 -sV 192.168.1.1
```
## aggressive scan
```bash
sudo nmap -A 192.168.1.1
```
```
nmap -sn 192.168.1.0/24
```

```
nmap -sn 192.167.1.0/24 | grep Nmap
```

```
nmap -sn 192.167.1.0/24 | grep Nmap | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}'
```

```
nmap -p 22 -sV $(nmap -sn 192.167.1.0/24 | grep Nmap | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}')
```

```
nmap -p 22 --script ssh2-enum-algos $(nmap -sn 192.167.1.0/24 | grep Nmap | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}')
```
# Firewall
REJECT or DROP

```
nmap -p 80 --reason -v 192.168.1.222 192.168.1.223
```

```
nc -zv 192.168.1.222 80
```
