```bash
stat test.txt
```

```bash
stat -c %y test.txt
```

```bash
stat -c "Modified: %y" test.txt
```

```bash
stat -c "Access: %x, Modify: %y, Change: %z" test.txt
```

```bash
stat -c $'Access: %x\nModify: %y\nChange: %z" test.txt
```

```bash
stat -c "%y %n" *.txt | sort -n
```
