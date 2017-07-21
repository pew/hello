# virtualbox

### change UUID hard disk
do not change a UUID of a vm/hard disk if there are snapshots available for thie machine. otherwise: fuckup

```
VBoxManage internalcommands sethduuid "path/to/disk"
```

### create new disk from snapshot
create a new disk from a snapshot. To use the new disk, simply create a new VM and use this disk as the existing disk.

```
VBoxManage clonehd ~/VirtualBox\ VMs/your-vm/Snapshots/\{581xe111-999b-48cd-a3c0-333b29ca123\}.vmdk newdisk.vmdk
```
