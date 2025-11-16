```bash
echo "Test text" | tr x s
```

delete all listed characters
```bash
echo "Test text" | tr -d ext
```

```bash
echo "Teest text" | tr -s e
```

```bash
echo "Test text" | tr "[:lower:]" "[:upper:]"
```

```bash
tr -d '\r' < test.txt | sort > test_out.txt
```

map complement of set1 to set2
```bash
tr -c set1 set2
```

