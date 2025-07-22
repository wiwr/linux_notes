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