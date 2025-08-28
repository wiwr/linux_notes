# Pre-checks
+ all VM that should start with server are set to yes for start after boot
+ set email notification
+ "reboot test" to check any issues with booting
# Installation
```bash
sudo apt update
```
```bash
sudo apt install unattended-upgrades -y
```
```bash
sudo dpkg-reconfigure --priority=low unatteded-upgrades
```
On configuration screen confirm to automatically download and install stable updates.

# Post installation checks
```bash
sudo systemctl status unattended-upgrades
```
# Configuraiton
```bash
cd /etc/apt/apt.conf.d
```
```bash
sudo vim 20auto-upgrades
```
Check if all options are set to `1`
```bash
cp 50unattended-upgrades 99unattended-upgrades
```
```bash
sudo vim 50unattended-upgrades
```
uncomment and change value if needed
```text
Unattended-Upgrade::AutoFixInterruptedDpkg "true";
Unattended-Upgrade::Mail "may@email.com";
Unattended-Upgrade::MailReport "only-on-error";
Unattended-Upgrade::Remove-Unused-Kernel-Packages "true";
Unattended-Upgrade::Remove-New-Unused-Dependencies "true";
Unattended-Upgrade::Remove-Unused-Dependencies "false"; 
Unattended-Upgrade::Automatic-Reboot "false"; //????
Unattended-Upgrade::Automatic-Reboot-WithUsers "true"; //????
Unattended-Upgrade::Automatic-Reboot_time "04:00"; //????
```
```bash
sudo systemctl edit apt-daily-upgrade.timer
```
Add section
```text
[Timer]
OnCalendar=*-*-* 3:00
RandomizedDelaySec=60m
Persistent=true
```
```bash
sudo systemctl daemon-reload
```
```bash
sudo systemctl restart unattended-upgrades
```
```bash
sudo systemctl status unattended-upgrades
```
```bash
sudo systemctl status apt-daily-upgrade.timer
```

# Symulation
```bash
sudo unattended-upgrade --dry-run --debug
```
