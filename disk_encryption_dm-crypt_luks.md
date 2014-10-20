# disk encryption dm-crypt luks
### install
    apt-get install cryptsetup

### prepare disk
    fdisk /dev/xvdd

### crypto crypto
    cryptsetup luksFormat -c aes-cbc-essiv:sha256 -s 256 /dev/xvdd
    cryptsetup luksOpen /dev/xvdd vault
    mkfs.ext4 /dev/mapper/vault

### mount
    mkdir /mnt/vault
    cryptsetup luksOpen /dev/xvdd vault
    mount /dev/mapper/vault /mnt/vault

### umount
    umount /mnt/vault
    cryptsetup luksClose /dev/mapper/vault

### backup header files
    cryptsetup luksHeaderBackup /dev/<device> --header-backup-file /mnt/<backup>/<file>.img

