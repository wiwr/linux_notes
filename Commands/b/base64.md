```bash
echo -n 'Hasło do mojego konta' | base64
```
```bash
SGFzxYJvIGRvIG1vamVnbyBrb250YQ==
```

```bash
base64 -d <<< SGFzxYJvIGRvIG1vamVnbyBrb250YQ== && echo
```

```bash
echo -n "XXXX" | base64 -w0
```