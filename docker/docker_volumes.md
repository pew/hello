# docker volumes
It's complicated somehow.

* [RTFM](https://docs.docker.com/engine/tutorials/dockervolumes/)

## create volume

```
docker create -v /root --name gmvault_data jonas/gmvault
```

use persistent data container in another container:

```
docker run -it --rm --name gmvault --volumes-from gmvault_data jonas/gmvault gmvault sync your@gmail.com
```

## backup a data container

```
docker run --rm --volumes-from gmvault_data -v $(pwd):/backup ubuntu tar cvf /backup/backup.tar /root
```