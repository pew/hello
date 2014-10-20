### install autossh
```
apt-get install autossh
brew install autossh
```
    
### tunnel example
    autossh -M -R 8888:localhost:22 user@middleman -p2222

### vnc tunnel example
#### @home
	autossh -M -R 8888:localhost:5900 you@server
    
##### @client
```
ssh root@hello -L 8888:localhost:8888
vnc://localhost:8888
```