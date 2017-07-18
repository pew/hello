# HAProxy websocket setup


```
defaults
  mode http
  log global
  option httplog
  option  http-server-close
  option  dontlognull
  option  redispatch
  option  contstats
  retries 3
  backlog 10000
  timeout client          25s
  timeout connect          5s
  timeout server          25s
# timeout tunnel available in ALOHA 5.5 or HAProxy 1.5-dev10 and higher
  timeout tunnel        3600s
  timeout http-keep-alive  1s
  timeout http-request    15s
  timeout queue           30s
  timeout tarpit          60s
  default-server inter 3s rise 2 fall 3
  option forwardfor
```

[source](http://www.haproxy.com/blog/websockets-load-balancing-with-haproxy/)