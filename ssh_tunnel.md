# ssh tunnel
### add linux user for ssh tunnel
```
adduser tunnel
usermod -s /bin/true tunnel
```

### interactive shell
    ssh root@target
    ~C

### ssh tunnel (socks proxy)
standard way:

    ssh tunnel@server -NT -D 127.0.0.1:8080

drop ssh in background:

    ssh tunnel@server -NTf -D 127.0.0.1:8080

now configure your os/application to use a SOCKS Proxy with the Address 127.0.0.1 and Port 8080

create a seperate user on the server, give the account _/bin/true_ as shell.

### ssh multihop
    ssh -A -t first-server ssh -A -t root@second-server ssh -A root@final-destination

### autossh proxy
```
autossh -f -M 20000 -D 8000 tunnel@host -N
autossh -M 0 -N user@server -D 1337 -o "IdentityFile /.ssh/key" -o "ServerAliveInterval 60"
```

### reverse / backward ssh tunnel
from external:

    ssh -R 4444:localhost:22 root@server

connect:

    ssh -p 4444 root@middleman

### multi hop port forwarding

```
ssh -L3333:localhost:3333 -L5555:localhost:5555 user@firsthop -t ssh -L3333:target:80 -L5555:target:443 pi@localhost -p2222
```
