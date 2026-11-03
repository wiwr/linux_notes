
### text file as script
```bash
who | awk '{ print $1 }' | sort | uniq | wc -l
```

```bash
bash script.txt
```
### awk script
```bash
#! /user/bin awk -f

BEGIN { print "hello, world!" }
```

```bash
awk -f hello.awk
```

### shell script
```bash
#! /bin/sh -

echo "Hello world!"
```

```bash
chmod +x hello.sh
```
```bash
./hello.sh
```

## Echo and read
```bash
#! /bin/bash

echo -n "Enter your name: "
read name
echo "Nice to meet you, $name."
```

### Arguments
```bash
$1..$9, $@, $*, "$@" and "$*"
```

```bash
#! /bin/bash
echo Processing $# arguments

count=1
while [ $# -gt 0 ]; do
	printf "\tArgument %d: '%s'\n" "$count" "$1"
	
	let "count = count + 1"
	shift
done
```