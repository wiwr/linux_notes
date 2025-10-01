```bash
rsync -av source destination
```
```bash
sudo apt install rsync -y
```

directory
```bash
rsync --dry-run -av ~/source_folder user@192.168.1.222:~/archive
```
directory content
```bash
rsync --dry-run -av ~/source_folder/ user@192.168.1.222:~/archive
```