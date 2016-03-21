# pf

### list rules in table:
```
pfctl -t TableName -T show
```

### add ip to table:
```
pfctl -t TableName -T add 1.2.3.4
```

### remove ip from table:
```
pfctl -t TableName -T delete 1.2.3.4
```



# pf example configuraiton
add to `/etc/pf.conf`

```
ext_if = "re0" # define external interface
pub_ip = "1.2.3.4" # define public ipv4

# main v6
root6 = "2a00:000:123:456::2" # define host ipv6

####################################
####  begin example jail config	####
####################################

#jail_net="192.168.2.0/24"
#jail_web_ip="192.168.2.2"
#jail_web="{80,443}"
 
#scrub in all
#nat pass on re0 from $jail_net to any -> $pub_ip
#rdr pass on re0 proto tcp from any to $pub_ip port $jail_web -> $jail_web_ip

####################################
####  end example jail config	####
####  note below for ipv6 jail	####
####################################

block all # okay

# allow jail and internal traffic
pass from { lo1, $jail_net } to any keep state # jail_net must be defined above and lo1 must be the cloned interface

# Allow SSH in to the host
pass in inet proto tcp to $pub_ip port ssh # allow v4
pass in inet6 proto tcp to $root6 port ssh # allow v6

## if ipv6 used
#pass in inet6 proto tcp to $jail_web_ip6 port $jail_web # allow v6 for web

# allow mosh
pass in inet proto udp to $pub_ip port 60000:60010

# allow ipv4 icmp
pass in on $ext_if inet proto icmp all icmp-type echoreq keep state
# allow ipv6 icmp
pass in on $ext_if proto icmp6

# Allow OB traffic
pass out all keep state
```

check config with

```
pfctl -nf /etc/pf.conf
```

restart pf

```
service pf restart
```