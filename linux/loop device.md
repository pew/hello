# loop device
mount a network share with smbfs, sshfs etc. and run rsync

## create image
mount the network share with smbfs or sshfs or whatever you have and create a image

```
dd if=/dev/zero of=/mnt/network-share/backup.img bs=1M count=10240
```

create a file system:

```
mkfs.ext4 /mnt/network-share/backup.img
```

## mount the image
mount the image to run rysnc for example:

```
mount -o loop /mnt/network-share/backup.img /mnt/backup
```

now you're able to rsync data from `/home` to `/mnt/backup/home` for example, even if there's no way on the remote share to use rsync.

## umount the image(s)
first, umount the image and the share afterwards

```
umount /mnt/backup
umount /mnt/network-share
```
