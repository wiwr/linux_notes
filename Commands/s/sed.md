Streamline editor

to change first occurrence
```bash
sed 's/unix/linux/' test.txt
```
specific number of occurrence (in this case 2)
```bash
sed 's/unix/linux/2' test.txt
```
start from specific occurrence (in that case 2)
```bash
sed 's/unix/linux/2g' test.txt
```
to update all occurrence
```bash
sed 's/unix/linux/g' test.txt
```
update in specific line (in that case 3)
```bash
sed '3 s/unix/linux/' test.txt
```
print updated line twice
```bash
sed 's/unix/linux/p' test.txt
```
print only updated lines
```bash
sed -n 's/unix/linux/p' file.txt
```
range of line
```bash
sed '1,3 s/unix/linux/' test.txt
```
delete a specific line
```bash
sed '2d' test.txt
```
delete last line
```bash
sed '$d' test.txt
```
to modife file 
```bash
sed -i '1d ' file.txt
```
use different delimiter 
```bash
sed 's|old|new|' test.txt
```
```bash
sed 's./etc..' test.txt
```

```bash
sed -e 's/:/---/g' /etc/passwd
```


