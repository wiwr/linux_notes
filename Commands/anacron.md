## anacron script
hello.sh
```bash
#!/bin/bash

# This is my anacron script

echo "Hello world!"

exit 0
```
```bash
chmod 755 hello.sh
```
## anacron path
```bash
cd /etc
```
```bash
ls -l cron*
```
## location where anacron keep information about last run
```bash
cd /var/soop/anacron
```
```bash
ls -l
```
```bash
sudo cat cron.daily cron.weekly cron. monthly
```