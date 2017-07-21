# supervisor(d)

```
pip install supervisor
```

# examples:

with environment variables:

```
[program:caddy]
environment=CLOUDFLARE_EMAIL="test@example.com",CLOUDFLARE_API_KEY="1337"
command=/usr/local/bin/caddy
directory=/home/me/
autostart=true
autorestart=true
startretries=3
stderr_logfile=/var/log/caddy.err.log
stdout_logfile=/var/log/caddy.out.log
user=me
```

python script in a virtual environment:

```
[program:myappName]
environment=PATH="/home/me/venv/app/bin"
command=/home/me/venv/app/bin/python /home/me/myapp/blab.py
directory=/home/me/myapp
autostart=true
autorestart=true
startretries=3
stderr_logfile=/var/log/myapp.err.log
stdout_logfile=/var/log/myapp.out.log
user=me
```
