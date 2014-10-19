# optimize os x

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

### disable swap (as root/sudo)
    launchctl unload -w /System/Library/LaunchDaemons/com.apple.dynamic_pager.plist
    rm /private/var/vm/swapfile*

#### re-enable swap in single user mod (cmd + s on boot):
    launchctl load /System/Library/LaunchDaemons/com.apple.dynamic_pager.plist

