# rename

mass renaming of files, exclude `.git`. it would rename all files containing an `_` and replacing it with a space.

```
find . -type f -not -path "*/.git*" -exec rename -S _ ' ' '{}' \;
```

withou the git exclusion:

```
find . -type f -exec rename -S _ ' ' '{}' \;
```
