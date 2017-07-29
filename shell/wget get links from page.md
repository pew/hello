# wget get links from page

```
wget -r --spider -l1 -A 7z https://archive.org/download/stackexchange 2>&1 | grep -Eio http.+7z
```

* `-r` - recursive
* `--spider` - just checkin', not downloading files
* `-l` - depth
* `-A` - *accept list* look for `7z` extension