To apply can be use:
```bash
exec bash
```

```bash

# Show a directory listing when using 'cd'
function cd() {
	new_directory="$*" # Save destination directory
	# When is empty/not set then go to home directory
	if [ $# -eq 0 ]; then
		new_directory=${HOME};
	fi;
	# use builtin cd not current function
	builtin cd "${new_directory}" && /bin/ls -lhF --time-style=long-iso --color=auto --ignore=lost+found
}
```