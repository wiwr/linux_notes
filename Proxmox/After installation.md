# Update repository
Set repository to No-Subscription and remove Subscription one
# Upgrade proxmox
Do system upgrade and reboot
# Update message
```bash
root@home:~# cd /usr/share/javascript/proxmox-widget-toolkit/
root@home:/usr/share/javascript/proxmox-widget-toolkit# ls -l
total 1152
drwxr-xr-x 2 root root   4096 Sep 18 18:20 css
drwxr-xr-x 2 root root   4096 Sep 18 18:20 images
-rw-r--r-- 1 root root 809300 Aug  4 15:50 proxmoxlib.js
-rw-r--r-- 1 root root 354913 Aug  4 15:50 proxmoxlib.min.js
drwxr-xr-x 2 root root   4096 Sep 18 18:20 themes
root@home:/usr/share/javascript/proxmox-widget-toolkit# cp proxmoxlib.js proxmoxlib.js.bkp
root@home:/usr/share/javascript/proxmox-widget-toolkit# vim proxmoxlib.js
-bash: vim: command not found
root@home:/usr/share/javascript/proxmox-widget-toolkit# vi proxmoxlib.js
root@home:/usr/share/javascript/proxmox-widget-toolkit# systemctl restart pveproxy
```

```javascript
        checked_command: function (orig_cmd) {
            orig_cmd();
            return;
            Proxmox.Utils.API2Request({
```

remember that can be in catch.
# Check network speed
```bash
ethtool enp2s0
```
look on:
```bash
        Speed: 1000Mb/s
        Duplex: Full
```
# Storage
add external storage
