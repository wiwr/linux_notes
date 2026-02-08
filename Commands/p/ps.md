```bash
ps -ef
```

```bash
ps -eo user,pid,ppid,cmd
```

```bash
ps -eo user,pid,ppid,cmd | bat -l bash --style=numbers
```

```bash
ps -ef -p 2
```

```bash
ps -ef | grep -v '\[\|]'
```

```bash
ps -fu <user>
```

```bash
ps -C pipewire
```

```bash
ps -C pipewire -f
```

```bash
ps -fC pipewire --deselect
```

```bash
export NORMAL_CMDS="zsh,bat,less,ps"
```
```bash
ps -f --ppid 1 -C $NORMAL_CMDS --deselect
```

```bash
ps ef --sort=start_time
```