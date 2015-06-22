# aws cli filter
## filter name
finds all `*sup*` instances

```
aws ec2 describe-instances --filters Name=tag:Name,Values=*sup*
```

## table view of all ec2 instances
credit ttps://github.com/aws/aws-cli/issues/368

```
aws ec2 describe-instances --query 'Reservations[].Instances[].[Placement.AvailabilityZone, State.Name, InstanceId,InstanceType,Platform,Tags.Value,State.Code,Tags.Values]' --output table
```
