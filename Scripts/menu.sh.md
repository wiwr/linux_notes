```bash
#!/bin/bash
x=0
while [ $x = 0 ]; do
	clear
	echo "Are you know what to do?"
	read answer
	
	case "$answer" in
		y) 
		echo "Good that you know."
		x = 1
		;;
		n) 
		echo "Not good. Check and do right thing"
		x=1
		;;
		*)
		clear
		echo "That is not right answer"
		sleep 5
		;;
	esac
done 
```