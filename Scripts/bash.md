Download file to temp file for vim
```bash
vim <(curl --please for ling to file--)
```

Compare sorted temporally files
```bash
diff <(sort file1.txt) <(sort file2.txt)
```

Check if changes will give expected output
```bash
diff file1.txt <(sed s/old_word/new_word/I file1.txt)
```


```bash
ls -l  >(cat)
```

to keep eye on processing of program
```bash
program > >(less) 2> >(tee errors.txt)
```

copy directory to two other servers
```bash
tar cf - directory | tee >(ssh server1 tar xf -) >(ssh 192.167.1.200 tar xf -) > /dev/null
```



