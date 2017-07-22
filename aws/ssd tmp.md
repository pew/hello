# aws ec2 ssd /tmp
```
# File /etc/init/ssd-tmp.conf
# ssd-tmp - Binds /tmp to /media/ephemeral0/tmp
description     "Binds /tmp to /media/ephemeral0/tmp"

start on starting rc RUNLEVEL=[35]

task

script
    test -d /media/ephemeral0/tmp || mkdir -m 1777 /media/ephemeral0/tmp
    mount --bind /media/ephemeral0/tmp /tmp
end script
```
