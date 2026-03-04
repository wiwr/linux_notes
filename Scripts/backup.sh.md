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
backup_dest="/mnt/backup/current"
current_date=$(date +%Y%m%d)
log_path="/mnt/backup/logs"
previous_files="/mnt/backup/files_previous/$current_date"

# Create required directories
mkdir -p "$log_path"
mkdir -p "$previous_files"

# Run rsync
rsync -av --delete --backup \
        --backup-dir="$previous_files" "$backup_src" "$backup_dest" \
        > "$log_path/backup_$current_date.log" \
        2> "$log_path/backup_${current_date}_error.log"
```