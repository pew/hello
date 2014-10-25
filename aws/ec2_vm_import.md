# ec2 vm import

# import instance or volume
    ec2-import-instance /vm/vm-disk1.vmdk -t m3.xlarge -f VMDK -a x86_64 -b some-name -o AWS_ACCESS_KEY -w AWS_SECRET_KEY -p Linux --region eu-west-1

    ec2-import-volume /vm/vm-disk1.vmdk -f vmdk -o AWS_ACCESS_KEY -w AWS_SECRET_KEY --region eu-west-1 -b some-name -z eu-west-1c

# with security group
    ec2-import-instance /vm/vm-disk1.vmdk -t m3.xlarge -g security-group-name -f VMDK -a x86_64 -b some-name -o AWS_ACCESS_KEY -w AWS_SECRET_KEY -p Linux --region eu-west-1

# with vpc
    ec2-import-instance /vm/vm-disk1.vmdk -t m3.xlarge --subnet subnet-49a8c77d -f VMDK -a x86_64 -b some-name -o AWS_ACCESS_KEY -w AWS_SECRET_KEY -p Linux --region eu-west-1
