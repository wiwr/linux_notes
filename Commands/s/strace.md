```bash
strace -tp `pgrep mintUpdate` 2>&1 | head -100
```