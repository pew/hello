# ipv6 debian / ubuntu

... because... reasons.

## manually

for testing or so:

```
ip -6 addr add 123:567:6:b00k::2/64 dev eth0
ip -6 route add 123:567:6:b00k::1 dev eth0
ip -6 route add default via 123:567:6:b00k::1 dev eth0
```

## persistent

`/etc/network/interfaces`

```
iface eth0 inet6 static
        address 123:567:6:b00k::2
        netmask 64
        gateway 123:567:6:b00k::1
```
