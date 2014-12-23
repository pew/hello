# resize disk lvm
## reduce disk size

for swap:

```
swapoff /dev/vg0/swap
lvreduce --size 2G /dev/vg0/swap
mkswap /dev/vg0/swap
swapon /dev/vg0/swap
```

## extend file system

```
vgchange -a y

vgdisplay
lvdisplay
swapoff /dev/vg0/swap
lvreduce --size 2G /dev/vg0/swap
mkswap /dev/vg0/swap
swapon /dev/vg0/swap

lvdisplay
vgdisplay
lvextend -l+100%FREE /dev/vg0/root
vgdisplay
resize2fs /dev/mapper/vg0-root
```
