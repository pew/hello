# ezjail

## update ezjail

```
mkdir /basejail
mount -t nullfs -o rw /usr/jails/basejail /basejail
ezjail-admin update -u
```
