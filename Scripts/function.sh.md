.bashrc file
```
source ~/.bash_prompt
source ~/.bash_aliases
source ~/.functions

count_files() {
	dir="${1:-.}"
	files=$(ls -1 "$dir" 2>/dev/null | wc -l)
	echo "There are $files files in directory: $dir"
}

```