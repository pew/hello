# disks - wat?

## mount: /dev/xvdf1 is already mounted or /sysroot busy

Mount disk on another system, remove those two files

```
rm /mnt/etc/blkid.tab
rm /mnt/etc/blkid.tab.old
```

## get label

```
e2label /dev/xvda1
```
