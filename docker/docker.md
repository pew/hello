# docker
* [cheat sheet](https://gist.github.com/wsargent/7049221)
* [docker compose](https://docs.docker.com/compose/)
* [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/)


## building
build docker image:

	docker build -t jonas/znc .
	
## running
run docker image with mounted data folder

```
docker run -d -p 60667 -v /home/jonas/.znc:/znc-data jonas/znc
```

## containers & images

### cleaning
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

---

# hands-on
get docker image

```
docker pull nginx
```

have a look into nginx docker image or a running container

```
docker ps # get the id
docker exec -i -t bb8658e2b9d0 /bin/bash
```

start docker image with mounted filesystem

```
docker run -v /docker/etc/nginx:/etc/nginx:ro -v /docker/var/www:/var/www:rw -p 80:80 -p 443:443 -d nginx
```

# backup / restore (export / import)

```
docker export c158164fxxx9 > nginx.tar
docker import - jonas/nginx < nginx.tar
```

to run a imported container and avoid `no command specified` start your imported container with a command:

```
docker run -d -p 80:80 -p 443:443 jonas/nginx nginx
```

# commit changes

```
docker commit c1237347 jonas/nginx
```

