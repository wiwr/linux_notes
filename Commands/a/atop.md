more advance monitoring tool
```bash
sudo apt install atop -y
```

logs for atop
```bash
vim /var/log/atop
```

```bash
atop -r /var/log/atop/atop_20260212
```

moves
"t" and "T" - move 20min
"b" to set time

configuration
```bash
vim /etc/sysconfig/atop
```