# syncthing

## get syncthing
* http://syncthing.net / https://github.com/syncthing/syncthing/releases/

## install syncthing
* extract the archive
* copy syncthing binary to $HOME/bin

```
mkdir $HOME/bin
cp syncthing $HOME/bin/
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

### on every syncthing installation again

* add/connect every devices via the *add device* button
* on your client installation, you can enter the hostname and port (example.com:22000) in the *Addresses* field if you have an server running all the time

### add folders
* add folders via the *add folder* button
* **configure** the **Share With Devices** part on **each** syncthing installation
* add *.DS_Store* to **ignore patterns** (if you're on a mac)

## debian init script
* after everything is configured and running, stop syncthing on your server instance and save the following script to */etc/init.d/syncthing*

```
#!/bin/sh
### BEGIN INIT INFO
# Provides: syncthing
# Required-Start: $local_fs $remote_fs
# Required-Stop: $local_fs $remote_fs
# Should-Start: $network
# Should-Stop: $network
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Multi-user daemonized version of syncthing.
# Description: Starts the syncthing daemon for all registered users.
### END INIT INFO

# Replace with users you want to run syncthing clients for
syncthing_USERS="jonas"
DAEMON=/home/jonas/bin/syncthing

startd() {
  for stuser in $syncthing_USERS; do
    HOMEDIR=$(getent passwd $stuser | awk -F: '{print $6}')
    if [ -f $config ]; then
      echo "Starting syncthiing for $stuser"
      start-stop-daemon -b -o -c $stuser -S -u $stuser -x $DAEMON
    else
      echo "Couldn't start syncthing for $stuser (no $config found)"
    fi
  done
}

stopd() {
  for stuser in $syncthing_USERS; do
    dbpid=$(pgrep -fu $stuser $DAEMON)
    if [ ! -z "$dbpid" ]; then
      echo "Stopping syncthing for $stuser"
      start-stop-daemon -o -c $stuser -K -u $stuser -x $DAEMON
    fi
  done
}

status() {
  for stuser in $syncthing_USERS; do
    dbpid=$(pgrep -fu $stuser $DAEMON)
    if [ -z "$dbpid" ]; then
      echo "syncthing for USER $stuser: not running."
    else
      echo "syncthing for USER $stuser: running (pid $dbpid)"
    fi
  done
}

case "$1" in
  start) startd
    ;;
  stop) stopd
    ;;
  restart|reload|force-reload) stopd && startd
    ;;
  status) status
    ;;
  *) echo "Usage: /etc/init.d/syncthing {start|stop|reload|force-reload|restart|status}"
     exit 1
   ;;
esac

exit 0
```
[source](https://discourse.syncthing.net/t/keeping-syncthing-running-systemd-regular-etc-init-d/402)
