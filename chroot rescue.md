# chroot rescue

```
mount /dev/nbd0 /mnt
mount -o bind /dev /mnt/dev
mount -t proc none /mnt/proc
mount -o bind /run /mnt/run
chroot /mnt /bin/bash
```