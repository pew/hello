# ipv6 freebsd

add to `/etc/rc.conf`

```
ipv6_default_interface="re0"
ifconfig_re0_ipv6="inet6 2axx:xxx:xxx:xxx::2/64"
ipv6_defaultrouter="fe80::1%re0"
```
