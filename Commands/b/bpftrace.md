```bash
sudo bpftrace -e 'tracepoint:syscalls:sys_enter_* { printf("%s\n", comm, str(args->filename)); }' ls
```