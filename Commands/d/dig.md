# dig
[[Linux/Network]]

```
alias dig='grc dig'
```

```bash
dig learnlinux.tv
```
```bash
dig learnlinux.tv MX
```
```bash
dig learnlinux.tv TXT
```
```bash
dig learnlinux.tv NS
```
```bash
dig @8.8.8.8 learnlinux.tv
```
```bash
dig +short learnlinux.tv
```
```bash
dig +ttl learnlinux.tv
```

```bash
dig wireshark.org +dnssec +bufsize=512
```

```bash
dig @a.root-servers.net wireshark.org +dnssec +bufsize=512
```

```
dig A google.com
```

```bash
dig A +noall +answer google.com
```

```bash
dig google.com TXT facebook.com MX instagram A
```

```bash
dig -f /path/file.list +short
```
```bash
dig -f /path/file.list +noall +answer
```

```bash
dig + trace google.com
```

