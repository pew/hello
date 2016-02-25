# irssi
awesome sauce

## initial setup
to be organized

```
# add network
/network add freenode

# add network with nickserv authentication
/network add -autosendcmd "/^msg nickserv ident user password;wait 5000" freenode

# add server to network
/server add -auto -ssl -network freenode chat.freenode.net 7070

# add channels (and join them automatically)
/channel add -auto #your-awesome-channel freenode

# save your layout
/layout save

# save config
/save
```

cheers!

## nickserv stuff
automatically authenticate against nickserv, wait 5 secs and join channels:

```
```



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