# hfs bit rot
```
find ~/ -type f -a ! -name '.DS_Store' -print0|xargs -0 shasum - > shasums.txt
shasum -c < shasums.txt  > check.txt
cat check.txt|fgrep -v OK
```

[link](http://blog.barthe.ph/2014/06/10/hfs-plus-bit-rot/)