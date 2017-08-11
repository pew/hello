# backup and restore docker volume

create a backup of volumes created with `docker volume`

## backup

```
docker run --rm -v test_gollum:/volume -v /tmp:/backup alpine tar cvf /backup/backup.tar /volume
```

* `test_gollum` - volume to be backed up
* `-v /tmp:/backup` mount local `/tmp/` to `/backup` in container

this command creates a `backup.tar` in `/tmp/`, so you might want to change the `tmp` part

## restore

```
docker run --rm -v testtest:/volume -v $(pwd):/backup alpine tar xvf /backup/backup.tar
```

* `testtest` - NEW volume name to restore to (was for testing purposes)
* `-v $(pwd):/backup` - mount current dir (in this case `/tmp/` to temporary docker container to restore `backup.tar`

# example

## backup all volumes

backup all `docker volumes` beginning with prefix `test`

```
for i in $(docker volume ls -f name=test -q); do docker run --rm -v $i:/volume -v /tmp:/backup alpine tar cvf /backup/$i.tar /volume;done
```

everything is backed up to `/tmp/CONTAINER_NAME.tar`

## restore all volumes

assuming you're in `/tmp/`

```
for i in *.tar;do docker run --rm -v ${i%%.*}:/volume -v $(pwd):/backup alpine tar xvf /backup/$i; done
```
