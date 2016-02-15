# renew let's encrypt cert

```
/root/.local/share/letsencrypt/bin/letsencrypt certonly --renew-by-default --agree-tos -a webroot -w /usr/local/www/ -d example.com -d www.example.com
```
