# docker
* [cheat sheet](https://gist.github.com/wsargent/7049221)
* [docker compose](https://docs.docker.com/compose/)
* [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/)


## building
build docker image:

    docker build -t jonas/znc .

## running
run docker image with a shared (mount) from the host system

```
docker run -d -p 60667 -v /home/jonas/.znc:/znc-data jonas/znc
```

## containers & images

ok.

### cleanup


remove one image

```
docker rmi the_image
```

remove all images except** 'my-image' and 'ubuntu':

```
docker rmi $(docker images | awk '$1!~/ubuntu|my-image/ && NR>1 {print $3}')
```

complete cleanup

```
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
docker rmi -f $(docker images -q -a)
```

#### remove unused images and container

they added this with some recent version:

```
docker image prune
docker system prune
```


## docker inspect

just run

```
docker inspect name
```

to get all information.

### inspect volumes

just get the mounts

```
docker inspect -f {{.Mounts}} name
```

# docker networking

create new network:

```
docker network create --driver bridge some-name
```

run container in new network:

```
docker run --network=some-name -itd --name=app ubuntu
```

run another container in same network:

```
docker run --network=some-name -itd --name=db postgres
```

If you `exec` or `attach` to the docker containers, they can ping each other. `ping app`, `ping db`
