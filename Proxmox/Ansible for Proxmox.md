# Create LXC Container
![[Pasted image 20260209173552.png]]
![[Pasted image 20260209173748.png]]
![[Pasted image 20260209173830.png]]
![[Pasted image 20260209173902.png]]
![[Pasted image 20260209173934.png]]
![[Pasted image 20260209174003.png]]
# Instalastion
```bash
apt update && apt upgrade -y
```
```bash
apt install ansible sshpass vim -y
```
# Check if Ansible works
```bash
ansible
```
# Create inventory
```bash
vim inventory.ini
```

```ini
[proxmox]
192.168.1.207
192.168.1.208
```

```bash
vim playbook.yml
```

```yml
- name: Update and Upgrade Proxmox
  hosts: proxmox
  tasks:
    - name: Update package list
      apt:
        update_cache: yes
        
    - name: Upgrade all packages
      apt:
        upgrade: dist
```

# Create fingerprint
login to each server or copy KHK.
# Run
```bash
ansible-playbook playbook.yml -i inventory.ini --ask-pass
```
 above can be run as script. With keys from crontab.
 