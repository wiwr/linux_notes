### SSH
```bash
ssh [opcje] [nazwa_użytkownika@]host [polecenie]
```
```bash
ssh server.admin.com "df -h /var/log"
```

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
