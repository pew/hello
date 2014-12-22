# ubuntu upgrade
## requirements
```
apt-get install update-manager-core
```

check */etc/update-manager/release-upgrades* for lts or normal release

## upgrade
```
do-release-upgrade
```

or silent update:

```
do-release-upgrade -f DistUpgradeViewNonInteractive
```

## check changed config files
```
find /etc/ -iname '*dpkg*'
```

diff them to apply changes

## housekeeping
```
apt-get --purge autoremove
apt-get clean all
apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')
```
