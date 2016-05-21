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

# notes
you should propbably store the key somewhere else

## resize (expand) file system
let's say the current filesystem is 25G and you want to resize it to 50G, use:

	dd if=/dev/zero of=/fs bs=1 seek=50G count=1
	# umount /mnt # maybe optional
	cryptsetup resize box
	resize2fs /dev/mapper/box
	mount /dev/mapper/box /mnt
	