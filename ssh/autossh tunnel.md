### install autossh
```
apt-get install autossh
brew install autossh
```

### monitoring port
disable the autossh monitoring port

```
-M 0
```

and use

```
-o "ServerAliveInterval 60" -o "ExitOnForwardFailure=yes" -o "ConnectTimeout 10"
```

instead

### tunnel example
```
autossh -M 0 -R 8888:localhost:22 user@middleman -p2222
```

with custom port

```
autossh -M 0 -q -f -N -o "ConnectTimeout 10" -o "ServerAliveCountMax 3" -o "ServerAliveInterval 60" -o "Port=1337" -o "ExitOnForwardFailure=yes" -R2222:localhost:22 user@server
```

### vnc tunnel example
#### @home

```
autossh -M 0 -R 8888:localhost:5900 you@server
```

##### @client
```
ssh root@hello -L 8888:localhost:8888
vnc://localhost:8888
```
