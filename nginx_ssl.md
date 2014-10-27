# nginx ssl
```
ssl						on;
ssl_certificate			/etc/nginx/ssl/bla.crt;
ssl_certificate_key		/etc/nginx/ssl/bla.key;
ssl_protocols			TLSv1 TLSv1.1 TLSv1.2;
ssl_prefer_server_ciphers on;
ssl_ciphers EECDH+AES128:RSA+AES128:EECDH+AES256:RSA+AES256:EECDH+3DES:RSA+3DES:EECDH+RC4:RSA+RC4:!MD5;
```