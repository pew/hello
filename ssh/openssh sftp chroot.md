# openssh sftp chroot

## sshd_config
```
vi /etc/sshd_config
```
```
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp

Match User awesome
    ForceCommand internal-sftp
    ChrootDirectory /home/awesome
```
```
service ssh restart
```

## user, groups & permissions

```
adduser awesome
usermod -s /bin/false awesome
chown root:awesome /home/awesome
chmod 750 /home/awesome
```

## create "write" folder
```
mkdir -p /home/awesome/data
chown -R awesome:awesome /home/awesome/data
```