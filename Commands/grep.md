### basic options
case insensitive
```bash
grep -i word file.txt
```
line number
```bash
grep -n word file.txt
```
find word not part
```bash
grep -w word file.txt
```
count findings
```bash
grep -c word file.txt
```
output only the results
```bash
grep -o word file.txt
```
invert match
```bash
grep -v word file.txt
```
recursive mode
```bash
grep -r word file.txt
```
to get context (2 before and/or after)
```bash
grep -C 2 word file.txt
```
```bash
grep -A 2 word file.txt
```
```bash
grep -B 2 word file.txt
```
### Regular expression

`grep -E` - Enhanced regular expression

to find lines that starts with given string
```bash
grep -E '^http' /etc/services
```
to find lines that ends with given string
```bash
grep -E 'http$' /etc/services
```
question mark makes the character before optional
```bash
grep -E '^https?' /etc/services
```
to find any whitespace character a space or a tab
```bash
grep -E '^https?\s' /etc/services
```
`.` represents any character and with `+` represents at least one character or more
```bash
grep -E '^https?\s+.+tc' /etc/services
```
