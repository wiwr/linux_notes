### Examples
#### Doom 
```bash
docker run kasmweb/doom:1.14.0
```
#### Web Server
```bash

```

#### btop
##### Docker file
```text
FROM alpine:latest

RUN apk update && \
    apk add --no-cache bash curl git build-base ncurses-dev
    
RUN git clone https://github.com/aristocratos/btop.git /opt/btop && \
    cd /opt/btop && \
    make && \
    make install
    
RUN apk del git build-base ncurses-dev && \
    rm -rf /var/cache/apk/* /opt/btop
    
CMD ["btop"]
```

```bash
docker build -t btop-image .
```