```
sudo apt install nmap
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

REJECT or DROP

```
nmap -p 80 --reason -v 192.168.1.222 192.168.1.223
```

```
nc -zv 192.168.1.222 80
```
