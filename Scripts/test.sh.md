```bash
x="hello world"
test "$x" = "hello world"
```
```bash
[ "$x" = "hello world" ] && echo "true"
```
```bash
if test "$x" = "hello world"; then echo "true"; fi
```
```bash
if [ "$x" = "hello world" ]; then echo "true"; fi
```
```bash
if  [[ $x = "hello world" ]]; then echo "true"; fi
```
```bash
if [[ $x =~ "hello" ]]; then echo "true"; fi
```