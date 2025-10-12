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
```bash
awk -F, '$3 > 50 {print $1, $2}' data.csv
```
```bash
awk 'BEGIN { RS=""; FS="\n"; ORS="\n\n" } {print $2,$3 }' data.log
```

```bash
awk '{print $3 "\t" $4}' input_file.txt
```
To print line match pattern
```bash
awk '/a/' input_file.txt
```
Print number of line that match pattern
```bash
awk '/a/{++cnt} END {print "Count = ", cnt}' input_file.txt
```
Count lines that contain more then n characters
```bash
awk 'length($0) > n' input_file.txt
```
```bash
awk 'BEGIN{printf "Name\tAmount\tPrice\n"}{print}' input_file.txt
```
variable
```bash
awk -v var=Test 'BEGIN{printf "Name = %s\n",name}'
```
global variables
```bash
awk --dump-variables ''
cat awkvars.out
```
```bash
awk 'BEGIN { num = 11; if (num % 2 == 0) printf "%d is even number.\n", num; else printf "%d is odd number.\n", num}'
```
```bash
awk 'BEGIN { for (i = 1; i <= 5; ++i) print i }'
```
```bash
awk 'BEGIN {i = 1; while (i < 6) { print i; ++i} }'
```
```bash
awk 'BEGIN {i = 1; do { print i; ++i } while (i < 6) }'
```
```bash
ps -ef | awk '{print $3, $5, $7}'
```
```bash
ps -ef | awk '{print $3 " --- " $5 " === " $7}'
```
```bash
ps -ef | awk 'BEGIN{printf "Col1\tCol2\tCol3\n"} {print $2"\t"$3"\t"$7} END{print "Done"}'  
```
grep with awk
```bash
ps -ef | awk ' /tty/ {print}'
```
```bash
ps -ef | awk '/test/{++c} END {print "Total matched: " , c}'
```
```bash
ps -ef | awk 'length($0) > 100 '
```
```bash
ps -ef | awk '{sub(/root/,"xxxxx");print}'
```
```bash
ps -ef | awk '{print $1; print $2}'
```

### if
```awk
x = 543
if (x == 111)
	print "It's 111";
else if (x == 456)
	print "It's 456";
else
	print "something else"
```
### array
```awk
array1["tree"] = "green";
array1["rock"] = "brown";
array1[23] = "red";
print array1["tree"] " " array1[23];
```
### delete from array
```awk
array1["abc"] = "xyz";
delete array1["abc"];
```
### for loop
```awk
for (c = 0; c <= 10; c++) print c
```
### while loop
```awk
c = 0; while (c <= 10) {print c; c++}
```
### do while loop
```awk
c = 0; do {print c; c++ } while (c <= 10)
```