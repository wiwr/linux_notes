```bash
rsync -av source destination
```
```bash
sudo apt install rsync -y
```

```bash
rsync Original/* Backup/
```

this sync content
```bash
rsync -r Original/ Backup/
```
and this folder with content
```bash
rsync -r Original Backup/
```

directory
```bash
rsync --dry-run -av ~/source_folder user@192.168.1.222:~/archive
```
directory content
```bash
rsync --dry-run -av ~/source_folder/ user@192.168.1.222:~/archive
```

to zip, archive and present progress bar
```bash
rsync -zaP /source_folder /destination_folder
```