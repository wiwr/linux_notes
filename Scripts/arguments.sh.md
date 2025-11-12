```bash
#!/bin/bash
printf 'Number of arguments is: %d\n\n' $#
printf 'First argument is %s\n\n' "$1"

echo '$*: All arguments are: ' $*
echo
echo '$@: All arguments are: ' $@
echo 
echo '"$*": All arguments are: ' "$*"
echo
echo '"$@": All arguments are: ' "$@"
echo
echo "### For loop ###"
count=1
for i; do
	printf "\tArgument %d: '%s'\n" "$count" "$i"
	let "count = count + 1"
done
echo "### While loop ###"
count=1
while [ $# -gt 0 ]; do
	printf "\tArgument %d: '%s'\n" "$count" "$1"
	let "count = count + 1"
	shift
done
```