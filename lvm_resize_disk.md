# resize disk lvm
## reduce disk size

for swap:

```
swapoff /dev/vg0/swap
lvreduce --size 2G /dev/vg0/swap
mkswap /dev/vg0/swap
swapon /dev/vg0/swap
```

---

## check
* resize vm disk
* check with fdisk if new "empty" space is found

## resize
	fdisk /dev/sda
	p
	n
	3
	return
	return
	p
	w
	
reboot the system

## resize part 2

	fdisk -l /dev/sda
	p
	
check if everything's ok

	pvcreate /dev/sda3
	vgs
	vgextend $volgroup /dev/sda3
	
check if free space is available:

	vgdisplay
	
if yes.. then resize:

	lvextend -L+500G /dev/mapper/vg_bla
    lvextend -l+100%FREE
	
then.... finally resize the filesystem

	resize2fs /dev/mapper/vg_bla
	
hopefully there is another (better) way to resize a lvm volume.