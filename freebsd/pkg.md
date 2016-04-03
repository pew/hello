# freebsd pkg

#### add, rm, update, upgrade packages

install packages:

```
pkg install package
```

uninstall packages:

```
pkg remove package
```

pkg update:

```
pkg update
```

upgrade packages

```
pkg upgrade
```

#### query (find, list) packages

search for a package:

```
pkg search dovecot
```

list all installed packages by name and version

```
pkg query %n-%v
```

have a look [here](https://www.freebsd.org/cgi/man.cgi?query=pkg-query&sektion=8#end)