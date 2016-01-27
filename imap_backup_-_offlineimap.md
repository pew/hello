# imap backup - offlineimap

## install offlineimap

freebsd:

```
pkg install offlineimap
```

## configuration
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
# path to ssl certs, freebsd example here
sslcacertfile = /usr/local/etc/ssl/cert.pem
```

be sure to have write access to the `localfolders` location

## backup

*interactive* mode:

```
offlineimap -c your-config-file
```

*cron* mode

```
offlineimap -c /path/to/your/config -u Noninteractive.Quiet
```