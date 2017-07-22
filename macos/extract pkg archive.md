# extract .pkg archive on mac os x
    pkgutil --expand file.pkg ~/path/to/extracted/contents

or just simply

```
tar xf bla.pkg
```

# one more thing

```
tar xf bla.pkg
cd payload.pkg
cat Payload|gunzip -dc|cpio -i
```

here you go
