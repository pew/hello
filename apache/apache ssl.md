# apache ssl
## vhost configuration

```
SSLEngine on
SSLProtocol all -SSLv2 -SSLv3

SSLHonorCipherOrder On
SSLCipherSuite ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DES-CBC3-SHA:HIGH:!aNULL:!eNULL:!EXPORT:!CAMELLIA:!DES:!MD5:!PSK:!RC4

SSLCertificateFile		/etc/apache2/ssl/bla.crt
SSLCertificateKeyFile	/etc/apache2/ssl/bla.key
SSLCertificateChainFile	/etc/apache2/ssl/ca.pem

Header add Strict-Transport-Security "max-age=15552000"
```

## redirect http to https
add this part to your *:80 (http) vhost config

```
RewriteEngine On
RewriteRule ^/?(.*) https://domain.tld/$1 [R=301,L]
```
