# ssh
## add / remote password from ssh-key
```
ssh-keygen -p
```

## forward ssh credentials
```
ssh -A user@host
```
```
ssh -A -t user@host ssh -A -t user@next-hop
```

## terminate ssh connection
```
[ENTER]
~.
```

## put ssh in background
```
[ENTER]
~[CTRL-z]
```
afterwards
```
fg
jobs
fg %1
```

## interactive ssh
```
[ENTER]
~C
```
