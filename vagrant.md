# vagrant
## create VM
Create new VM in VirtualBox or VMware Fusion, set **Network Adapter 1** to **NAT**.

NAT Settings:

```
Name: SSH
Host Port: 2222
Guest Port: 22
```

## install OS & configure VM
* install VirtualBox Tools
* install with the following *metadata*

```
Root PW: vagrant
User: vagrant
Password: vagrant
```

### set up access rights

```
sudo su - root
visudo
```

```
Defaults:vagrant !requiretty
Defaults env_keep = "SSH_AUTH_SOCK"
vagrant ALL=NOPASSWD: ALL
```

### get vagrant key
```
mkdir -p /home/vagrant/.ssh
chmod 0700 /home/vagrant/.ssh
wget https://raw.github.com/mitchellh/vagrant/master/keys/vagrant.pub -O /home/vagrant/.ssh/authorized_keys
chmod 0600 /home/vagrant/.ssh/authorized_keys
chown -R vagrant /home/vagrant/.ssh
```

## create vagrant box
```
mkdir ~/vagrant/
cd ~/vagrant/
vagrant package --base YOUR-VirtualBox-VM-Name
```