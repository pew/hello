# aws packer.io
* install [packer](http://packer.io/)

## get image id
```
ec2-describe-images|grep IMAGE|grep instance-name|awk '{print $2}'
```

## packer example.json
```
{
  "variables": {
    "aws_access_key": "ASDFASDFASDF",
    "aws_secret_key": "asdfasdf44441111",
    "ami": ""
  },
  "builders": [{
    "type": "amazon-ebs",
    "access_key": "{{user `aws_access_key`}}",
    "secret_key": "{{user `aws_secret_key`}}",
    "region": "eu-west-1",
    "source_ami": "{{user `ami`}}",
    "instance_type": "m3.large",
    "ssh_username": "root",
    "ssh_private_key_file" : "/root/.ssh/id_rsa",
    "ami_name": "new-ami-name {{uuid}}",
    "tags": {
      "Name": "new-ami-name",
      "Servicegroup": "web"
    },
    "launch_block_device_mappings": [{
      "device_name": "/dev/xvda",
      "volume_size": 100,
      "volume_type": "standard",
      "delete_on_termination": true
    }]
  }],
  "provisioners": [{
      "type": "shell",
      "inline": [
        "sleep 300",
        "yum update -y",
	    "history -c",
	    "rm /root/.bash_history"
    ]
  }]
}
```

example with script as provisioner:

```
{
  "variables": {
    "aws_access_key": "ASDFASDFASDF",
    "aws_secret_key": "asdfasdf44441111",
    "ami": ""
  },
  "builders": [{
    "type": "amazon-ebs",
    "access_key": "{{user `aws_access_key`}}",
    "secret_key": "{{user `aws_secret_key`}}",
    "region": "eu-west-1",
    "source_ami": "{{user `ami`}}",
    "instance_type": "m3.large",
    "ssh_username": "root",
    "ssh_private_key_file" : "/root/.ssh/id_rsa",
    "ami_name": "new-ami-name {{uuid}}",
    "tags": {
      "Name": "new-ami-name",
      "Servicegroup": "web"
    },
    "launch_block_device_mappings": [{
      "device_name": "/dev/xvda",
      "volume_size": 100,
      "volume_type": "standard",
      "delete_on_termination": true
    }]
  }],
  "provisioners": [{
    "type": "shell",
    "script": "/home/packer/scripts/maintenance.sh"
  }]
}
```

## run packer script
```
packer build example.json
packer build -debug example.json
packer build -var ami=ami-id example.json
```