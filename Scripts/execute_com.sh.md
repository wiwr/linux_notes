```bash
#!/bin/bash
name=`whoami`
echo $name
```

```bash
#!/bin/bash
name=$(whoami)
echo $name
```

```bash
#!/bin/bash
printf '<%s>\n' $(uptime)
```

```bash
#!/bin/bash
printf '<%s>\n' "$(uptime)"
```

```bash
#!/bin/bash
echo <(uname)
```

```bash
#!/bin/bash
cat <(uname)
```


