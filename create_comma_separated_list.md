# comma separated list from list

```
cat bla.txt|tr -s ' ' | cut -d ' ' -f 2 | tr '\n' ',' | sed 's/,$//'
```
