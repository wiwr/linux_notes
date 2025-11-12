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
```