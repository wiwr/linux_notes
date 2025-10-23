```bash
find
```

```bash
find /
```

```bash
find / -name httpd.conf
```

```bash
find /home -type d -name logs
```

```bash
find . -type d
```

```bash
find . -type f
```

```bash
find . -type f -name "test.txt"
```

```bash
find . -type f -name "test*"
```
case insensitive 
```bash
find . -type f -iname "test*"
```

```bash
find . -type f -mmin -10
```

```bash
find . -type f -mmin +1 -mmin -5
```

```bash
find . -size +5M
```

```bash 
find . -perm 777
```

```bash
find / -user root
```

```bash
find / -type f ! -user root
```

```bash
find . -exec chown user:group {} \;
```

```bash
find . -type d -exec chmod 775 {} \;
```

```bash
find . -type f -exec chmod 664 {} \;
```

```bash
find . -type f -name "*.jpg" -maxdepth 1 -exec rm {} \;
```

```bash
find /var -type f -name "*.log" | xargs grep "error"
```