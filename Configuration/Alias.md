### To find IP
correctly works for single IP
```bash
alias myIP="echo $(ifconfig | grep broadcast | awk '{print $2}')"
```
correctly works for multiple IP
```bash
alias myIP='ifconfig | grep broadcast | awk "{print \$2}"'
```

