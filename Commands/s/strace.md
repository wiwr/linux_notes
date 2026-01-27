```bash
strace -tp `pgrep mintUpdate` 2>&1 | head -100
```

```bash
strace ls -l 2>&1
```

```bash
strace -e%file ls -l 2>&1 | less
```

```bash
strace -f -e%file ls -l 2>&1 
```