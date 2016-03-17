# Create new jail with ezjail
First, create a new jail and assign an IP address. Maybe even IPv6:

```
ezjail-admin create jailname 172.16.1.2
ezjail-admin create jailname "lo1|172.16.1.2,vtnet0|2A03:B0C0:0003:00D0:0000:0000:0110:1"
```

set an alias in `/etc/rc.conf`

```
ifconfig_lo1_alias1="inet 172.16.1.2 netmask 255.255.255.255"
```

to enable the alias immediately:

```
ifconfig lo1 alias 172.16.1.2 netmask 255.255.255.255
```

copy a resolv.conf file to the new jail for DNS resolution:

```
cp /etc/resolv.conf /usr/jails/znc/etc/
```

Start new jail:

```
ezjail-admin start jailname
```

