```bash
who | awk '{ print $1 }' | sort | uniq
```

```bash
who | sed 's/[^[:alnum:]].*//' | sort | uniq
```

