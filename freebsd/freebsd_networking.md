# networking
## ipv6 tunnelbroker (he.net)

add to `/etc/rc.conf`

```
# IPv6
ipv6_gateway_enable="YES"
ipv6_interfaces="auto"
ipv6_activate_all_interfaces="YES"
ipv6_cpe_wanif="gif0"
cloned_interfaces="gif0"
ipv6_defaultrouter="2001:666:1f04:666::1"
ifconfig_gif0="tunnel your_ipv4_server he.net_ipv4_server"
ifconfig_gif0_ipv6="inet6 2001:470:1f04:4d6::2 prefixlen 128"
```

for aliases, add to `/etc/rc.conf`:

```
ifconfig_gif0_alias0="inet6 2001:666:1f04:666::3 prefixlen 128"
ifconfig_gif0_alias1="inet6 2001:666:1f04:666::4 prefixlen 128"
```

## pf.conf, if used

add protocol 41  to `/etc/pf.conf`

```
# allow tunnelbroker
pass in on $ext_if inet proto 41 from he.net.ipv4 to your.ip.v4
pass out on $ext_if inet proto 41 from your.ip.v4 to he.net.ipv4
```
