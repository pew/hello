# backup and restore docker volume

### backup

```
docker run --rm --volumes-from ContainerName -v $(pwd):/backup alpine tar cvf /backup/backup.tar /var/jenkins_home
```

* runs an `alpine` docker container
* bind mount `$(pwd):/backup`
* run `tar` of `/var/jenkins_home` to `/backup/backup.tar`

### restore

either you have a container (with volume) already or create one with `docker volume create`, you also need a container running. quick example:

```
docker run -v testvol:/var/jenkins_home -d alpine ping 8.8.8.8
```

(this command created `jovial_wozniak`)

```
docker run --rm --volumes-from jovial_wozniak -v $(pwd):/backup alpine tar xvf /backup/backup.tar
```

check the files:

```
docker exec -it jovial_wozniak ls -l /var/jenkins_home
```

gg