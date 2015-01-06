### install autossh
```
apt-get install autossh
brew install autossh
```
    
### tunnel example
```
autossh -M -R 8888:localhost:22 user@middleman -p2222
```

with custom port

```
autossh -M 0 -q -f -N -o "ServerAliveCountMax 3" -o "StrictHostKeyChecking=no" -o "Port=1337" -R2222:localhost:22 user@server
```

### vnc tunnel example
#### @home
	autossh -M -R 8888:localhost:5900 you@server
    
##### @client
```
ssh root@hello -L 8888:localhost:8888
vnc://localhost:8888
```