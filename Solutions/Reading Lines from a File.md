#  Bash Script
This script reads and prints each line from `list.txt`.
```bash
# !/bin/bash

input_file="list.txt"

if [[ ! -f "$input_file" ]]; then 
	echo "File not found: $input_file" exit 1 
fi

while IFS= read -r line; do 
	echo "$line" 
done < "$input_file" 
```
# Bash Function
```bash
print_file_lines() {
    local file="$1"

    if [[ ! -f "$file" ]]; then
        echo "File not found: $file"
        return 1
    fi

    while IFS= read -r line; do
        echo "$line"
    done < "$file"
}
```

```bash
print_file_lines "list.txt"
```

