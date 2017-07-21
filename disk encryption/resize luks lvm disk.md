# resize luks lvm disk

##### check sector length

```
parted /dev/vda
	unit s
	p
```

##### resize partitions

```
parted /dev/vda
	unit s
	resizepart 2
	
parted /dev/vda resizepart
	unit s
	resizepart 5
```

##### verify new length

```
parted /dev/vda
	unit s
	print
```

##### mount and resize luks

```
cryptsetup luksOpen /dev/vda5 vda5_crypt
cryptsetup resize vda5_crypt
```

##### resize lvm part

you may want to change the names.

```
vgscan --mknodes
vgchange -ay
pvresize /dev/mapper/vda5_crypt
lvresize -l +100%FREE /dev/bender-vg/root
resize2fs /dev/mapper/bender--vg-root
```