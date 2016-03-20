# install ezjail

```
pkg install ezjail
```

enable ezjail and pf (natting) by adding the following to `/etc/rc.conf`

```
ezjail_enable="YES"
pf_enable="YES"
```

start ezjail right now

```
service ezjail start
```

initial basejail installation

```
ezjail-admin install
```

# prepare network configuration
add the following to `/etc/rc.conf`

I'm assuming we have to NAT to each jail since our server only has one public IPv4

```
cloned_interfaces="lo1"
ipv4_addrs_lo1="192.168.2.0/24"
```

start the cloned interface right now

```
service netif cloneup
```

# prepare pf.conf

add to `/etc/pf.conf`

you may have to adapt the IP addresses

```
pub_ip="1.2.3.4"
jail_net="192.168.2.0/24"

jail_web_ip="192.168.2.2"
jail_web="{80,443}"
 
scrub in all
nat pass on re0 from $jail_net to any -> $pub_ip
rdr pass on re0 proto tcp from any to $pub_ip port $jail_web -> $jail_web_ip
```

I'm using `jail_web_ip` and `jail_web` for the `web` jail aka webserver. This way I have a cool name schema for additional jails. `jail_ftp` for example

load rules and start pf

```
pfctl -nf /etc/pf.conf
service pf start
```

check the rules:

```
pfctl -sn
```

**note**: the pf.conf is only for natting, no incoming traffic will be filtered
