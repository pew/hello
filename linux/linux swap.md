## swap fstab
```
/swap none    swap    sw    0   0
```

## swappiness
```
cat /proc/sys/vm/swappiness
sysctl vm.swappiness=20
echo 'vm.swappiness = 20' >> /etc/sysctl.conf
```
