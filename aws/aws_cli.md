# aws cli

## query instance data
get AvailabilityZone, State & ID

```
aws ec2 describe-instances --query 'Reservations[*].Instances[*].[Placement.AvailabilityZone, State.Name, InstanceId]' --output text
```

get ID

```
aws ec2 describe-instances --query 'Reservations[*].Instances[*].[InstanceId]' --output text
```

get public ip

```
aws ec2 describe-instances --instance-ids $instanceidSeeAbove --output text --query 'Reservations[*].Instances[*].PublicIpAddress'
```

---

[source](http://alestic.com/2013/11/aws-cli-query)

## start instance
```
instance_id=$(aws ec2 run-instances --region us-east-1 --key $USER --instance-type t1.micro --image-id ami-d9a98cb0 --output text --query 'Instances[*].InstanceId')
echo instance_id=$instance_id
```

## while loop until instance is running
```
while state=$(aws ec2 describe-instances --instance-ids $instanceid --output text --query 'Reservations[*].Instances[*].State.Name'); test "$state" = "pending"; do
  sleep 1; echo -n '.'
done; echo " $state"
```