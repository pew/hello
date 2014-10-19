# /etc/init/bla.conf
startup script
```
start on runlevel [2345]
stop on runlevel [!2345]
exec su - gollum -c /home/gollum/start.sh
```