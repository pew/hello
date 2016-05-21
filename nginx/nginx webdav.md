# nginx webdav

```
server {
	listen 80 default_server;
	listen [::]:80 default_server;

	location / {
	  if ($request_method = POST) {
	  # use temporary to allow for POST to go through
	  # 301 will only work for GET/HEAD/OPTIONS
	    return 307 https://$host$request_uri;
	  }
	  return 301 https://$host$request_uri;
	}
}

server {
	listen 443 default_server;
	listen [::]:443 default_server;

	client_max_body_size 0;

	ssl on;
	ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
	ssl_prefer_server_ciphers on;
	ssl_ciphers "EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH";
	ssl_ecdh_curve secp384r1;
	ssl_session_cache shared:SSL:10m;
	ssl_session_tickets off;
	ssl_stapling on;
	ssl_stapling_verify on;
	resolver 8.8.8.8 8.8.4.4 valid=300s;
	resolver_timeout 5s;
	add_header Strict-Transport-Security "max-age=63072000; includeSubdomains; preload";
	add_header X-Frame-Options DENY;
	add_header X-Content-Type-Options nosniff;

	ssl_certificate /etc/letsencrypt/live/domain/fullchain.pem;
	ssl_certificate_key /etc/letsencrypt/live/domain/privkey.pem;

	location / {
	  #try_files $uri $uri/ /index.html;
	  root      /var/www/box;
	  client_body_temp_path /mnt/tmp;
	  dav_methods		PUT DELETE MKCOL COPY MOVE;
	  dav_ext_methods	PROPFIND OPTIONS;
	  create_full_put_path  on;
	  dav_access    group:rw all:rw;
	  autoindex     on;
	  auth_basic "restricted";
	  auth_basic_user_file /etc/nginx/htpasswd;
	}
}
```