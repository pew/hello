# set locale system wide

edit `/etc/login.conf` and add `:lang=en_US.UTF-8:` to the *default* block:

```
default:\
        :lang=en_US.UTF-8:\
        :passwd_format=sha512:\
        :copyright=/etc/COPYRIGHT:\
        :welcome=/etc/motd:\
```

```
cap_mkdb /etc/login.conf
```

logout, login, tada!
