# create ansible template files

get config without comments

```
grep -v ^# /etc/sshd_config > sshd_config.j2
```

make your changes, add variables (see ansible docu), for example:

```
#{{ ansible_managed }}
Port 22
ListenAddress {{ ansible_ssh_host }}
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
UsePrivilegeSeparation yes
```

