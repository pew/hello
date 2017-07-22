# get AMI ID
* [documentation](http://docs.aws.amazon.com/cli/latest/reference/ec2/describe-images.html#examples)

```
aws ec2 describe-images --filters "Name=is-public,Values=false" "Name=name,Values=your-image-name" --output=text|grep IMAGE|grep your-image-name|awk '{print $5}'
```

# run EC2 instance
* [documentation](http://docs.aws.amazon.com/cli/latest/reference/ec2/run-instances.html#examples)

```
aws ec2 run-instances --image-id ami-c3b8d6aa --count 1 --instance-type t1.micro --key-name MyKeyPair --security-groups MySecurityGroup
```

e.G.

```
ami=$(aws ec2 describe-images --filters "Name=is-public,Values=false" "Name=name,Values=your-image-name" --output=text|grep IMAGE|grep your-image-name|awk '{print $5}')
aws ec2 run-instances --image-id $ami --count 1 --instance-type m3.large --security-group-ids sg-xxxxx --subnet-id subnet-xxxx
```