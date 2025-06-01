```bash
awk '{print $2}'
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
