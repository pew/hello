# requirements

* [see important steps/requirements for creating a new base vm](https://docs.vagrantup.com/v2/virtualbox/boxes.html)

# vagrantfile

```
$ cat Vagrantfile
Vagrant.configure("2") do |config|
  config.vm.network "forwarded_port", guest: 9000, host: 9000

  config.vm.box = "box-name"
  config.vm.hostname = "hostname"

  config.ssh.port = "2222"
  config.ssh.private_key_path = "insecure_vagrant_key"

  config.vm.provider :virtualbox do |vb|
    vb.customize [
      "modifyvm", :id,
      "--memory", "4096",
    ]
  end
end
```

I defined memory settings for the VM, an own ssh key instead of the one provided by vagrant.

# create image
Get the name from your current VM in VirtualBox and execute

```
vagrant package --base vmname
```