# imap backup - offlineimap

## install offlineimap

freebsd:

```
pkg install offlineimap
```

## example: backup IMAP account
### configuration
create config file somewhere

```
[general]
accounts = fastmail

[Account fastmail]
localrepository = Local
remoterepository = Remote

[Repository Local]
type = Maildir
localfolders = /home/you/mail

[Repository Remote]
type = IMAP
remotehost = your.imapserver.com
remoteuser = username@domain.com
remotepass = your$super-duper,secure@password
ssl = yes
realdelete = no
createfolders = no
# path to ssl certs, freebsd example here
sslcacertfile = /usr/local/etc/ssl/cert.pem
```

be sure to have write access to the `localfolders` location

execute the backup either in

*interactive* mode:

```
offlineimap -c your-config-file
```

or *cron* mode

```
offlineimap -c /path/to/your/config -u quiet
```

## example: migrate account
in this case from IMAP to GMail

### configuration
this configuration will migrate from fastmail (strange, huh?) (remote repository) to gmail (local repository).

```
[general]
accounts = sync
maxsyncaccounts = 1

[Account sync]
localrepository = gmail
remoterepository = fastmail

[Repository gmail]
type = IMAP
remotehost = imap.gmail.com
remoteuser = user@gmail.com
remotepass = your-pw
ssl = yes
realdelete = no
sslcacertfile = /usr/local/etc/ssl/cert.pem

[Repository fastmail]
type = IMAP
remotehost = mail.messagingengine.com
remoteuser = user@fastmail.com
remotepass = your-pw
ssl = yes
realdelete = no
sslcacertfile = /usr/local/etc/ssl/cert.pem
readonly = true
```

and run the script:

```
offlineimap -c your-config-file
```
