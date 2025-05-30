```bash
#!/bin/bash 

if [ ! -e host.txt ]; then 
    echo "host list missing" 
    exit 1 
fi 

[ -e hostsFound.txt ]  && rm hostsFound.txt 

for h in $(cat host.txt); do 
   ssh user@${h} <command> >> hostsFound.txt 
done

diff host.txt hostsFound.txt
```
Required to provide host.txt with hosts.