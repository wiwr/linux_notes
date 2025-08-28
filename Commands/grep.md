


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
