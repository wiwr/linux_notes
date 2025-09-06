Streamline editor

to change first occurence
```bash
sed 's/unix/linux/' test.txt
```
to update all
```bash
sed 's/unix/linux/g' test.txt
```
use different delimiter 
```bash
sed 's|old|new|' test.txt
```
```bash
sed 's./etc..' test.txt
```