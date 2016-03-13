# add swap space
## create swap file

```
dd if=/dev/zero of=/usr/swap0 bs=1m count=256
```

```
chmod 0600 /usr/swap0
```

## enable swap
add to `/etc/fstab`

```
md99	none	swap	sw,file=/usr/swap0	0	0
```

```
swapon -aL
```

see: https://www.freebsd.org/doc/handbook/adding-swap-space.html
