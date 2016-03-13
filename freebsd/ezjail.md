# ezjail

## using ezjail
### login to jail

```
ezjail-admin console <name>
```

### start / stop jail

```
ezjail-admin start <name>
ezjail-admin stop <name>
ezjail-admin restart <name>
```

## backup and restore jail

```
ezjail-admin archive <name>
ezjail-admin archive -f <name>
```

restore:

```
ezjail-admin restore -f name-201512311522.07.tar.gz name
```

## updating jails

```
mkdir /basejail
mount -t nullfs -o rw /usr/jails/basejail /basejail
ezjail-admin update -u
```
