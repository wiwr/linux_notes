```bash
curl https://demotywatory.pl
```
```bash
curl -X POST https://demotywatory.pl
```
```bash
curl -X POST --data "key1=value1&key2=value2" https://demotywatory.pl
```
```bash
curl -X POST -d key1=value1 -d key2=value2 https://demotywatory.pl
```
```bash
curl -o response https://demotywatory.pl
```
with header
```bash
curl -I https://demotywatory.pl
```
send with header
```bash
curl --header "Content-type:applicaton/json" -X POST -d key1=value1 https://demotywatory.pl
```

jokes
```bash
curl https://official-joke-api.appspot.com/jokes/ten
```