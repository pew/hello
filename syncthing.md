# syncthing

## get syncthing
* http://syncthing.net / https://github.com/syncthing/syncthing/releases/

## install syncthing
* extract the archive
* copy syncthing binary to /usr/local/bin

```
cp syncthing /usr/local/bin/
```

## start & configure syncthing
* do every step once on your server and afterwards on your client
* start syncthing by executing *syncthing* in your shell

```
syncthing
```
* syncthing will create a initial configuration and start your browser pointing at http://localhost:8080/

### client
* open the webpage, open the settings, set the following for the client:

![image](https://github.com/pew/hello/blob/master/.assets/syncthing_client.png)

* tl;dr: **disable**
	* local discovery
	* global discovery
	* start browser

### server
* and this for the server:

![image](https://github.com/pew/hello/blob/master/.assets/syncthing_server.png)

* tl;dr: **disable**
	* enable upnp
	* local discovery
	* global discovery
	* start browser

* add/connect every devices via the *add device* button
* on your client installation, you can enter the hostname and port (example.com:22000) in the *Addresses* field