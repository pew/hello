# nginx proxy
... with http auth

```
server {
    listen       443 ssl;
    server_name  wiki.example.yo;

    ssl_certificate      /etc/nginx/certs/yo.crt;
    ssl_certificate_key  /etc/nginx/certs/yo.key;

    ssl_session_cache shared:SSL:50m;
    ssl_session_timeout 10m;

    ssl_ciphers AES256+EECDH:AES256+EDH:!aNULL;
    ssl_prefer_server_ciphers on;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    add_header Strict-Transport-Security "max-age=31536000; includeSubdomains";
    add_header X-Frame-Options DENY;
    add_header X-Content-Type-Options nosniff;

    location / {
        proxy_pass http://localhost:4567/;
        auth_basic "Restricted";
        auth_basic_user_file /etc/nginx/pw;
    }
}
```
