
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

