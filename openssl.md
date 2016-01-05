# openssl

### create csr
    openssl req -nodes -newkey rsa:4096 -keyout myserver.key -out myserver.csr

### encrypt a file
    openssl enc -aes-256-cbc -salt -in file.txt -out file.enc

### decrypt a file
    openssl enc -d -aes-256-cbc -in file.enc

### remove key from key
    openssl rsa -in www.key -out new.key

### connect
    openssl s_client -connect your.server.com:993

### view certificate
    openssl x509 -in certificate.crt -text

## create CA for webserver
```
cd /etc/ssl/private
openssl genrsa -des3 -out yourdomain.key 4096

openssl req -new -x509 -days 3065 -key yourdomain.key -out yourdomain.crt

openssl genrsa -des3 -out you.key 4096
openssl req -new -key you.key -out you.csr

openssl x509 -CA yourdomain.crt -CAkey yourdomain.key -CAcreateserial -days 720 -req -in you.csr -out you.pem

openssl pkcs12 -export -out you.pfx -inkey you.key -in you.pem -certfile yourdomain.crt

# Client auth via certs
ssl_client_certificate /etc/ssl/private/yourdomain.crt;
ssl_trusted_certificate /etc/ssl/private/yourdomain.crt;
ssl_verify_client on;

location / {
    if ($ssl_client_s_dn !~* "you@yourdomain.com") {
        return 301 http://www.jurassicsystems.com/;
    }
    error_page 403 @fallback;
}
```

[source (wohoo!)](http://arstechnica.com/information-technology/2014/04/taking-e-mail-back-part-4-the-finale-with-webmail-everything-after/4/)

# check expiration date

```
openssl s_client -connect hostname.lan:port | openssl x509 -noout -dates
```
