# irssi
awesome sauce

## initial setup
to be organized

```
/network add freenode
/server add -auto -ssl -network freenode chat.freenode.net 7070
/layout save
/save
```

cheers!

## scripts
create the needed folder structure:

```
mkdir -p $HOME/.irssi/scripts/autorun
```

download your scripts to

```
$HOME/.irssi/scripts/
```

symlink the scripts you want to load automatically while starting irssi to `scripts/autorun`

for example:

```
ln -s ~/.irssi/scripts/trackbar.pl ~/.irssi/scripts/autorun/
```