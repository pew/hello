# create encrypted file system

create new file for future file system

	dd if=/dev/zero of=/fs bs=1 seek=25G count=1

generate key

	dd if=/dev/urandom of=/fs.key bs=1 count=32
	
mount filesystem with `cryptsetup`

	cryptsetup luksFormat --key-file=/fs.key /fs
	cryptsetup luksOpen --key-file=/fs.key /fs box

create filesystem on new disk

	mkfs.ext4 /dev/mapper/box
	
actually mount filesystem

	mount -o loop /dev/mapper/box /mnt

# yo
you should propbably store the key somewhere else