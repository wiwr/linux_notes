```bash
awk '{print $2}'
```
```bash
arp -a | awk '{OFS="\t"; print $7, $4, $2, $1}' | sort -k 4 | grep -v incomplete 
```
