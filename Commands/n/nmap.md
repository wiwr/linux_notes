# Installation
```
sudo apt install nmap
```
# Scans
Single destination
```bash
nmap 192.168.1.222
```
Information about system
```bash
namp -O 192.168.1.222
```
Do only ping for network
```bash
nmap -sP 192.168.1.222
```
```bash
nmap -sP 192.168.1.0/24 | grep "Nmap scan" | awk '{ print $5 }'
```
## specific ports
for single
```bash
nmap -p22 192.168.1.1
```
for multiple ports
```bash
nmap -p22-25 192.168.1.1
```

```bash
nmap -v -A 192.168.1.222
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
```bash
nmap -sn --open 192.168.1.0/24
```
```bash
nmap -sn --open 192.168.1.0/24 --exclude 192.168.1.1
```
```
nmap -sn 192.167.1.0/24 | grep Nmap
```

```
nmap -sn 192.167.1.0/24 | grep Nmap | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}'
```
## run nmap with addresses from file
```bash
nmap --sn --open -iL iplist.txt
```

## save also output
in all three formats
```bash
nmap --sn --open -iL iplist.txt -oA output
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

## Script engine

```bash
nmap -sV -sC -v 192.168.1.222
```
```bash
nmap -sV --script=http-malware-host -p443 192.168.1.222
```

## More verbose
```bash
nmap -vv 192.168.1.222
```