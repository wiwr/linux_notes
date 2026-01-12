### SSH
```bash
ssh [opcje] [nazwa_użytkownika@]host [polecenie]
```
```bash
ssh server.admin.com "df -h /var/log"
```

### Update configuration
``
### Pass user
```bash
ssh -l hsolo@server.admin.com
```
or 
```bash
ssh hsolo@server.admin.com
```

```bash
ssh -i ~/.ssh/id_ecdsa hsolo@server.admin.com
```

```bash
ssh -o StrictHostKeyChecking=no server.admin.com
```

```bash
ssh -h
```


### Port forwarding
```bash
ssh -L 8000:webserver:80 server.admin.com
```
# Tunneling SSH
```
ssh user@192.168.1.22 -D 12345
```
12345 = port
### first option
In application set connection settings to used Host SOCK5: `127.0.0.1` and port `12345` and make sure that DNS is also.
### second option
install `proxychains`
```bash
sudo vim /etc/proxychains4.conf
```
change to 
```text
socks5 127.0.0.1 12345 
```
```bash
sudo porxychains nmap -sT -Pn --top-ports 10 192.168.1.22
```

## create key
`~/.ssh/id_rsa` - Private Key
`~/.ssh/id_rsa.pub` - Public Key
`authorized_keys` - on server keys are in that file
```bash
ssh-keygen -t rsa -b 4096
```
## copy key to server
```bash
ssh-copy-id user@host_or_ip
```
