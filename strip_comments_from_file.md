# strip comments from file

```
cat /etc/openvpn/server.conf | sed '/^#/ d'
```

# strip comments and empty lines from file

```
cat /etc/openvpn/server.conf | sed '/^#/ d;/^$/d'
```
