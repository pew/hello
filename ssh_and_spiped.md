# ssh + spiped

### generate private key and start spiped
* @server:

```
dd if=/dev/urandom bs=32 count=1 of=/etc/ssh/spiped.key
spiped -d -s '[0.0.0.0]:8022' -t '[127.0.0.1]:22' -k /etc/ssh/spiped.key
```

### setup client
* install spiped on client

```
brew install spiped
```

* copy spiped.key key to your local machine to *~/.ssh/spiped_HOSTNAME_key*
* add this to *~/.ssh/config*:

```
Host HOSTNAME
    Hostname hostname/ip
    User root
    ProxyCommand spipe -t %h:8022 -k ~/.ssh/spiped_%h_key
```

or

```
Host HOSTNAME
    Hostname hostname/ip
    User root
    IdentityFile /private/.ssh/id_rsa
    ProxyCommand spipe -t %h:8022 -k /private/.ssh/spiped_%h_key
```

* then just ssh to your host

[source](http://www.daemonology.net/blog/2012-08-30-protecting-sshd-using-spiped.html)