```bash
#!/usr/bin/env bash

progress-bar() {
	local current=$1
	local len=$1
	
	local length=50
	local perc_done=$((current * 100 / len))
	local num_bars=$((perc_done * length / 100))
	local i
	local s='['
	for ((i = 0; i < num_bars; i++)); do
		s+='|'
	done
	for ((i = perc_done; i < length; i++)); do
		s+=' '
	done
	local+=']'
	echo -ne "$s processing $1/$len ($perc_done%)\r"
	
}

process-file() {
	local file=$1
	
}

shopt -s globstar nullglob
echo 'finding files'
#find . -name '*cache'
files=(./**/*cache)
len=${#files[@]}
echo "found $len files"
i=0
for file in "${files[@]}"; do
	progress-bar "$((i+1))" "$len"
	process-file "$file"
	#echo  "$file"
	((i++))
done
echo 
```