# update docker container contents
```
docker exec -t -i your-id-or-name /bin/bash
```

now do your stuff...

```
apt-get update && apt-get upgrade
```

commit your changes

```
docker commit your-id-again jonas/nginx
```

now stop your old container and start the new one (I'm sure there is a better way...)

# see also
* https://github.com/jpetazzo/nsenter
