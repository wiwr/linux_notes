Calculate previous month and set year. Also if needed update year
```bash
MONTH=$(date +%m)
[ $MONTH -eq "01" ] && MONTH=12 || ((MONTH--))
MONTH=`printf %02d $MONTH`
YEAR=$(date +%Y)
[ $MONTH -eq "12" ] && ((YEAR--))
```