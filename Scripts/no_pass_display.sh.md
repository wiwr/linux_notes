```bash
#!/bin/bash
pass1=x pass2=y
until [ "$pass1" = "$pass2" ]; do
	stty -echo
	printf "Enter new password: "
	read pass1 < /dev/tty
	printf "\nEnter again: "
	read pass2 < /dev/tty
	stty echo
	echo
	if [ "$pass1" = "$pass2" ]; then
		echo "Passwords match"
	else
		echo "Passwords do not match"
	fi
done
```