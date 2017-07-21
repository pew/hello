# pipes
## pipe through the internetz
	dd if=/dev/sda1 bs=4096 conv=notrunc,noerror | ssh 10.10.10.10 dd of=/home/meaneye/backup.img bs=4096
	
	tar -cf /dev/stdout /path/to/files | gzip | ssh user@host 'tar -zxvf /dev/stdin -C /path/to/remote/files'
	
	tar -cz /path/to/files | ssh user@host tar -xz -C /path/to/remote/files
	
	tar -czf - /path/to/files | ssh user@host tar -xzf - -C /path/to/remote/files