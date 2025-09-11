```bash
awk '{print}' file.txt
```
```bash
awk '{print $2}' file.txt
```
```bash
arp -a | awk '{OFS="\t"; print $7, $4, $2, $1}' | sort -k 4 | grep -v incomplete 
```
```bash
awk -F, '$3 > 50 {print $1, $2}' data.csv
```
```bash
awk 'BEGIN { RS=""; FS="\n"; ORS="\n\n" } {print $2,$3 }' data.log
```
```bash
awk '/gcc/ {print $1}' file.txt
```
```bash
awk '/^w/ {print $1}' file.txt
```

```bash
vim script.awk
```
```awk
func round(0) {
   n = n + 0.5
   n = int(n)
   return n
}
func printlist(n) {
   for(i=1;1<=n;i++) {
       printf("%d ", i)
   }
}
{printlist($)}
/gcc/ {print $1}
/^w/ {print $1}
print int($1)
print round($2)
```
```bash
awk -f script.awk file.txt
```
```bash
awk 'NR==1; NR>1{printf("%.1f %c\n",($2=="F" ? ($1-32) / 1.8 : $1)," C")}' temps.csv
```
```csv
temp unit
26.1 C
23.1 C
100 F
85 F
23.3 C
```
```bash
awk '{print "First column item: " $1 " Second column item: " $2 }' temps.csv
```
```bash
awk '($0 ~ /e$/){print $0}' animals.txtW!tek1984

```