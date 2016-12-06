# aws cli queries

## query for instance name, ID, private and public IP

```
aws ec2 describe-instances --output text --query 'Reservations[*].Instances[*].[Tags[?Key==`Name`].Value|[0], InstanceId, PublicIpAddress, PrivateIpAddress]'
```
