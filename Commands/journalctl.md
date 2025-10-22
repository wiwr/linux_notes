```bash
sudo journalctl
```

```bash
sudo journalctl -xe
```

### kernel
```bash
sudo journalctl -k
```

```bash
sudo journalctl -u apache
```

```bash
sudo journalctl -f
```

```bash
sudo journalctl --disk-usage
```

```bash
sudo journalctl --since "2025-10-01 00:00:00" --until "2025-10-21 00:00:00"
```

```bash
sudo journalctl -p err
```

```bash
sudo journalctl -n 20
```

```bash
sudo journalctl --no-page
```

```bash
sudo journalctl -o verbose
```

```bash
sudo journalctl -o json
```

```bash
sudo journalctl -o json-pretty
```

```bash
sudo journalctl --list-boots
```

```bash
sudo journalctl -b -1
```

```bash
sudo journalctl --vacuum-time=2d
```

```bash
sudo journalctl --vacuum-size=10M
```
