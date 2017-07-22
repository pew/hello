# overwrite dhcp provided nameserver
... on ubuntu, edit `/etc/dhcp/dhclient.conf`

```
prepend domain-name-servers 127.0.0.1;
```
