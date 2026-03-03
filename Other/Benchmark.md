# GSmartControl
```bash
sudo apt install gsmartcontrol
```

Open in GUI
Right click on drive to scan and then Perform Test

# CPU
```bash
lscpu | grep -i bogo
```

# Memory
## memtester
```bash
sudo apt install memtester
```

```bash
memtester
```

```bash
sudo memtester 2G 1
```

## memtest86+
```bash
sudo apt install memtest86+
```

Then ESC with start

# System
```bash
sudo apt install sysbench
```

```bash
sysbench cpu --threads=$(nproc) run
```

# Stress test
```bash
sudo apt install stress-ng
```

```bash
stress-ng --cpu 0 --io 2 --vm 1 --vm-bytes 1G --timeout 120s --metrices-brief
```

```bash
watch "sensors"
```

# glmark2
```
sudo apt install glmark2
```

```bash
glmark2
```

# logs
```bash
sudo dmesg -l err,crit
```

# nvidia
```
watch -n 1 nvidia-smi
```