# replace line containing string

change `daemonize = true;` in prosody.cfg.lua to `daemonize = false;` by searching for `daemonize` and replacing the whole line

```
sed -i '/daemonize/c\daemonize = false;' /etc/prosody/prosody.cfg.lua
```
