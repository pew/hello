# network communication between two docker compose projects

let's say you have a reverse proxy in one docker-compose project and a webapp in another compose project.

you want network communication between the proxy and your webapp, and between the webapp and the sql server in the docker-compose project.

* proxy (compose project a) <-> webapp (compose project b)  
* webapp (compose project a) <-> sql (compose project b)
* no communication between the proxy and sql server.

this `docker-compose.yml` excerpt is from our webapp, the other project is just running in a folder called `proxy`, hence the network name `proxy_default`.

```
services:
  webapp:
    links:
      -mysql
    networks:
      - proxy
      - web

   mysql:
    image: mysql
    networks:
      - web

networks:
  proxy_default:
    external: true
  web:
```

your container(s) in the proxy compose project can now just `ping` webapp but not `mysql`. If the database is not needed, just get rid of the `web` network