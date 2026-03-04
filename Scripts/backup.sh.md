```
#!/bin/bash

backup() {
        local description="$1"
        local file="$2"
        local tar_options="$3"
        local source="$4"
        echo "$description"
        time tar "$tar_options" "$file" "$source"
        echo -n "File: $(basename "$file") Size: "
        ls -lh "$file" | awk '{ print $5 }'
		echo "Task completed."
}

backup "Backup file with tar" "Backup.tar" "-cf" "toBackup.txt"

```


# backup.sh
```bash
#!/bin/bash

backup_src="/home/witek"
backup_mount="/mnt/backup"
backup_dest="$backup_mount/current"
current_date=$(date +%Y%m%d)
log_path="$backup_mount/logs"
previous_files="$backup_mount/files_previous/$current_date"

# use when run with mounted directory
#if ! mountpoint -q $backup_mount; then
#       echo "Backup directory is not mounted! Exiting!"
#       exit 1
#fi

# Create required directories
mkdir -p "$log_path"
mkdir -p "$previous_files"

# Run rsync
rsync -av --delete --backup \
        --backup-dir="$previous_files" "$backup_src" "$backup_dest" \
        > "$log_path/backup_$current_date.log" \
        2> "$log_path/backup_${current_date}_error.log"
```

```bash
sudo chown root:root /usr/local/bin/backup.sh
```

```bash
sudo vim /etc/systemd/system/backup.service
```
```bash
[Unit]
Description=Run a daily backup
After=network-online.target
Wants=netowrk-online.target

[Service]
Type=oneshot
ExecStart=/usr/local/bin/backup.sh

[Install]
WantedBy=timers.target
```

```bash
sudo vim /etc/systemd/system/backup.timer
```
```bash
[Unit]
Description=Daily rsync backup timer

[Timer]
OnCalendar=00:00
Presistent=true

[Install]
WantedBy=timers.target
```

```bash
sudo systemctl daemon-reload
```
```bash
systemctl status backup.timer
```
```bash
sudo systemctl enable --now backup.timer
```
```bash
systemctl status backup.timer
```
```bash
sudo systemctl start backup.service
```
```bash
systemctl status backup.service
```