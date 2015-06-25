# optimize os x

## disable swap

```
sudo nvram boot-args="vm_compressor=2"
```

additionally (if you want):

```
sudo pmset -a hibernatemode 0
sudo rm -rf /private/var/vm/*
sudo chflags uchg /private/var/vm/
```

### disable hibernation mode mac os x (as root/sudo)
	pmset -a autopoweroff 0
	pmset -a hibernatemode 0
	pmset -a standby 0
	pmset -a standbydelay 0
	rm /var/vm/sleepimage

	touch /private/var/vm/sleepimage
	chflags uchg /private/var/vm/sleepimage

#### re-enable hibernation mode
10.9 defaults:

	Currently in use:
	standbydelay         4200
	standby              1
	hibernatemode        3
	autopoweroff         1

	rm /var/vm/sleepimage
