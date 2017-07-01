# unlock luks encrypted disk remotely via ssh

install dropbear and busybox

```
apt-get install dropbear busybox
```

create folders, since they're not created always

```
mkdir -p /etc/initramfs-tools/etc/dropbear
```

generate host keys

```
dropbearkey -t dss -f /etc/initramfs-tools/etc/dropbear/dropbear_dss_host_key
dropbearkey -t rsa -f /etc/initramfs-tools/etc/dropbear/dropbear_rsa_host_key
dropbearkey -t ecdsa -f /etc/dropbear-initramfs/dropbear_ecdsa_host_key
```

edit `/etc/initramfs-tools/initramfs.conf` and enable busybox and assuming DHCP is used to get the IP address, change `DEVICE` to your network interface. `eth0` or something

```
BUSYBOX=y
DEVICE=ens4
```

put your public ssh key(s) here:

```
/etc/dropbear-initramfs/authorized_keys
```

update your config:

```
update-initramfs -u -k all
```

reboot your system and unlock the disk like so:

```
ssh -o UserKnownHostsFile="/dev/null" -i ~/.ssh/id_rsa root@1.2.3.4 'echo -ne "unlockPassphrase" >/lib/cryptsetup/passfifo'
```

the docs:

* `/usr/share/doc/dropbear-initramfs/README.initramfs`
* `zcat /usr/share/doc/cryptsetup/README.Debian.gz`