# docker
[cheat sheet](https://gist.github.com/wsargent/7049221)
## building
**build docker image**

	docker.io build -t jonas/znc .
	
## running
**run docker image with mounted data folder**

	docker.io run -d -p 60667 -v /home/jonas/.znc:/znc-data jonas/znc

## images	
### removing
**remove one image**

	docker rmi the_image

**remove all images**

	docker rmi $(docker images -q)

**remove all images except** 'my-image' and 'ubuntu':

	docker rmi $(docker images | awk '$1!~/ubuntu|my-image/ && NR>1 {print $3}')

---

# hands-on
get docker image

```
docker pull nginx
```

have a look into nginx docker image

```
docker run -t -i nginx /bin/bash
```

start docker image with mounted filesystem

```
docker run -v /docker/etc/nginx:/etc/nginx:ro -v /docker/var/www:/var/www:rw -p 80:80 -p 443:443 -d nginx
```