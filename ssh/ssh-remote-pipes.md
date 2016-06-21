# ssh remote pipes

stuff

## ssh jump host

stolen from [here](https://www.reddit.com/r/sysadmin/comments/4oxxgv/your_favorite_scripts_you_have_stolen_or_made/d4gp1qo), put into your `~/.ssh/hosts` file and run `ssh first+second+finalhost`

```
Host *+*
  ProxyCommand ssh $(echo %h | sed 's/+[^+]*$//;s/\([^+%%]*\)%%\([^+]*\)$/\2 -l \1/;s/:/ -p /') nc -q0 $(echo %h | sed 's/^.*+//;/:/!s/$/ %p/;s/:/ /')
```

## file transfer scp & rsync

more stuff

### ssh / scp middleman
	ssh -o ProxyCommand='ssh myfirsthop nc -w 10 %h %p' mydestination
	scp -o ProxyCommand='ssh middleman nc -w 10 %h %p' admin@target:"~/test/*" .
	rsync -avxiP -e "ssh -o ProxyCommand='ssh middleman nc -w 10 %h %p'" admin@target:~/test/ .

### tar push
    ssh root@server "tar -cjf - /etc" > /Volumes/backup/etc.tar.bz2

    tar cpf - /opt/corpus | ssh root@1.3.3.7 "tar xpf - -C /"

    tar cf - music/|ssh server 'cat - > /tmp/music.tar'
### tar pull
    ssh -o ProxyCommand='ssh user@middleman nc -w 10 %h %p' user@target "tar cpf - /opt"|tar xvf - -C /

### extract tar
```
cat bla.tgz|ssh host tar -xzf - -C /opt/restore/
```
	
## commands
### run shell commands
    command="/usr/local/bla.sh $SSH_ORIGINAL_COMMAND",no-port-forwarding,no-x11-forwarding,no-agent-forwarding, ssh-rsa publickeyhere
