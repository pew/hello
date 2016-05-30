# kvm / libvirt /virsh troubleshooting
I have no idea.

## todo

* get an idea

# install kvm

```
apt install qemu-kvm libvirt-bin virtinst libguestfs-tools
```

# create a VM

You should adapt the `name`, `ram`, `disk-name` and so on. I think I found it [here](https://raymii.org/s/articles/virt-install_introduction_and_copy_paste_distro_install_commands.html#Debian_8) with some customizing.

```
virt-install \
--name VM-name \
--ram 1024 \
--disk path=./disk-name.qcow2,size=10 \
--vcpus 2 \
--os-type linux \
--os-variant generic \
--graphics none \
--console pty,target_type=serial \
--location 'http://ftp.us.debian.org/debian/dists/jessie/main/installer-amd64/' \
--extra-args 'console=ttyS0,115200n8 serial'
```

# create template

clone disk

```
virt-clone --original vmNAME --name newNAME --file filename.img
```

ready for starting!

---

prepare vm **caution** - something's still wrong o/

```
virt-sysprep -d vmNAME
```

---

prevent template-vm from auto-booting

```
virsh autostart --disable vmNAME
```

# commands

list running vm's:

```
virsh list
```

list all vm's:

```
virsh list --all
```

start / stop / reboot

```
virsh start <name> # start
virsh start <name> --console # start with console -- see below if you hang at 'ramdisk'
virsh reboot <name> # reboot
virsh shutdown <name> # shutdown
virsh destroy <name> # force shutdown
```

list dhcp leases:

```
virsh net-dhcp-leases default
```


## troubleshooting
ok!

### 'default' network not available

Requested operation is not valid: network 'default' is not active

```
virsh -c qemu:///system net-autostart default
virsh -c qemu:///system net-start default
```

### boot hangs at *loading ramdisk*

while in grub, hit `e` and append `console=ttyS0` to the `linux` part in the bootloader. When logged in then, fix it by running:

```
systemctl enable getty@ttyS0
```