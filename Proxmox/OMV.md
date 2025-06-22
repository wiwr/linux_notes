## Dashboard


## Passthrough a SATA drive to an OMV VM
```bash
lsblk
```
```bash
qm list
```
```bash
qm stop <vmid>
```
```bash
ls -l /dev/disk/by-id/
```
```bash
qm set <vmid> -scsi1 /dev/disk/by-id/<your-disk-id>
```
```bash
qm start <vmid>
```